---
title: "Wireless network goes slow in time"
date: 2007-01-14
forum: Networking &amp; Wireless
---

### Post by listerthrawn on 2007-01-14
Hi,

I have a Dell Inspiron 6400 laptop.  I'm generally pleased with Ubuntu on it but for a couple of things.

Mainly is my wireless connection going slow.

It's an Intel 3945 wireless card.  I can't explain it.  If I copy a large file (~2Gb) it starts off well at 2.5 Mb a second (as shown in System Monitor).  After a while it will just slow up to 100K a second.  From this point there is nothing I can do to speed it up.  It is slow for all traffic.  If I ifdown eth1 and ifup eth1 the speed returns for a while.

I've attached an image that describes the problem

Signal strength doesn't appear to be the problem

The network is WPA protected and I've used network manager and just plain wpa_supplicant with /etc/network/interfaces but its still the same.

Has anyone else experienced this?

---

