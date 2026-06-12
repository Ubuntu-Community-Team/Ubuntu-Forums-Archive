---
title: "remote desktop via webpage"
date: 2008-04-10
forum: Networking &amp; Wireless
---

### Post by thimerion on 2008-04-10
Hi, 

I followed following procedure to setup a webpage which I can use to take over my pc:

[http://ubuntuforums.org/showthread.php?t=107503](http://ubuntuforums.org/showthread.php?t=107503)

It works fine from any browser,
but it doesn't work, if the browser is configured to use a proxy server to access the internet, and if the internet only can be accessed via that proxy server.

Any idea's.

Tim

---

### Post by sammy_pal on 2008-04-13
When you use a proxy server only port 80 (http) and perhaps port 443(https) traffic are sent through the proxy server. The Java VNC viewer need some other port ( perhaps 5900) to establish connection to the VNC server. That's why you are not able to access your VNC server from a machine which has to access internet only through a proxy server.

---

