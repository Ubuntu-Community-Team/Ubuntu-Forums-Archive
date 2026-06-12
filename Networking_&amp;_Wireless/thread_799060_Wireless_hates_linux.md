---
title: "Wireless hates linux"
date: 2008-05-18
forum: Networking &amp; Wireless
---

### Post by IzThatHawt7 on 2008-05-18
Hello there...
When i have finally downloaded 8.04 and installed it, my amazement was endless: my wireless network card worked absolutely fine after i agreed to install the offered driver for it, and i have completely switched to linux because of that. However, scary things began happening after about two weeks: many ntworks could be found, but none could be connected to. The problem is neither in router nor in malfunctioning card: under windows it works ok. What should i do, and what could be the cause? 

Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02).

And yeah, a network interface called "wmaster-0" appears with wlan interface. It wasn't happening before. =/

---

### Post by Cenotaph on 2008-05-18
I'm a BCM4318 owner myself and although the b43 driver is an improvement over the old bcm43xx, i'd recommend you use the ndiswrapper driver to setup your card as it is more stable.

Follow this guide:

[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

---

