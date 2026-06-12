---
title: "connecting to both wired and wireless networks"
date: 2007-11-08
forum: Networking &amp; Wireless
---

### Post by mardawi on 2007-11-08
Hi guys,

How do i connect to a wired network to access other machines connected to the same network and connect to a different wireless network to access the internet were i have a faster internet connection?

---

### Post by HermanAB on 2007-11-08
Set the default route to the wireless gateway - something like this:
$ sudo route add default gw 192.168.x.y wlan0

That way, traffic to the local subnet on eth0 will go over the LAN and traffic to anything not on the LAN will go out to the gateway on wlan0.

Cheers,

Herman

---

