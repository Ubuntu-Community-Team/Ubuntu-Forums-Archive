---
title: "How to get proxy autoconfiguration URL"
date: 2017-07-09
forum: Networking &amp; Wireless
---

### Post by Shaktijar on 2017-07-09
Hallo.
Since the proxy was installed on our corporate network I didn't had an URL for PAC-file for configuring the system proxy settings.
I used [http://manpages.ubuntu.com/manpages/zesty/man1/pactester.1.html ]("http://manpages.ubuntu.com/manpages/zesty/man1/pactester.1.html")
The output of ```
curl -s http://wpad/wpad.dat | pactester -p - -u http://google.com

``` is *proxy.hostname.ru:3130*.
Is it a http-,  shttp-, ftp- or Socks-proxy, or all together?
May by I am to put ***proxy.hostname.ru/proxy.pac ***as Autoconfguration URL in Network Proxy Preferences?

---

