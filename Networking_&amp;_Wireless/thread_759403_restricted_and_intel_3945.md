---
title: "restricted and intel 3945"
date: 2008-04-19
forum: Networking &amp; Wireless
---

### Post by toha on 2008-04-19
I am wondering why Ubuntu seems to have problems with wireless connection. I have tried PClinuxOC and intel 3945 driver works with a restricted connection at once.

I like Ubuntu most and therefore it is a shame that I can only use my laptop on open connection as my own is restricted. I have had the problem with 7.10 and now with 8.04.

Anyone who knows the reason why ubuntu have these problems with wireless?

---

### Post by xradarx on 2008-04-19
[http://ipw3945.sourceforge.net](http://ipw3945.sourceforge.net)

---

### Post by Zorael on 2008-04-19
I couldn't get my second 3945 circuit to work at all (first one was a breeze, so revision differences), until I found [this automatic installer](http://linuxwireless.org/en/users/Download). See if it works.

---

### Post by chili555 on 2008-04-19
I don't think a different driver is the answer. My 3945 works perfectly with a restricted network. Here is the eth1 portion of my */etc/network/interfaces* file with some details changed to protect the innocent:```
auto eth1
iface eth1 inet dhcp
wireless-essid myrouter
wireless-key 012345xxx **restricted**
```Good luck and let us know.

---

