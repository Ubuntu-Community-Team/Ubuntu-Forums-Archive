---
title: "openconnect on ubuntu 14.04LTS I get “XML response has no ”auth“ node”"
date: 2014-08-26
forum: Networking &amp; Wireless
---

### Post by tomerbd on 2014-08-26
I run openconnect to connect to juniper as following

$ openconnect --version
OpenConnect version v5.02
Using GnuTLS. Features present: PKCS#11, TOTP software token, DTLS (using OpenSSL)


```
sudo openconnect -v -u=myuser --no-xmlpost --no-proxy https://myserver

Got HTTP response: HTTP/1.1 200 OK
Content-Type: text/html; charset=utf-8
Date: Mon, 25 Aug 2014 07:24:03 GMT
x-frame-options: SAMEORIGIN
Pragma: no-cache
Cache-Control: no-store
Expires: -1
Transfer-Encoding: chunked
HTTP body chunked (-2)
XML response has no "auth" node
Failed to obtain WebVPN cookie
```

can anyone help please?

(also asked [here]("http://superuser.com/questions/802571/openconnect-on-ubuntu-14-04lts-i-get-xml-response-has-no-auth-node"))

---

