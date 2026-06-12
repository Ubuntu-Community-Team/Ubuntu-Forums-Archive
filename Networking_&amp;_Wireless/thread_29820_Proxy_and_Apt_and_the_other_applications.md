---
title: "Proxy and Apt and the other applications"
date: 2005-04-26
forum: Networking &amp; Wireless
---

### Post by Jagec on 2005-04-26
Hello to everyone!

I'm having an issues with setting up my internet wireless conection over proxy. I saw man apt.conf but whatever I do, it doesn't work on my /etc/apt/apt.conf. How to set Apt working over proxy server? All proxy servers are 192.168.2.100 and port is 8000. And there is an user name and password as well. And that's all what I need.

Is it possible to set up proxy servers on system basis to avoid setting up every single application?

Thank you.

---

### Post by GrumpySmurf on 2005-04-26
You should be able to use the dante SOCKS client to connect through the proxy server.  

```
$ sudo apt-get install dante-client
```
More information about dante can be found here:

[http://www.inet.no/dante/](http://www.inet.no/dante/)

The /etc/socks.conf is well documented.

---

