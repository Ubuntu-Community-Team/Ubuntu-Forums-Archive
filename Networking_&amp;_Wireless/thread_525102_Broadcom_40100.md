---
title: "Broadcom 40100"
date: 2007-08-13
forum: Networking &amp; Wireless
---

### Post by kevindubrow on 2007-08-13
Hi, I just bought a Gateway MX7118 laptop off of eBay and have installed Ubuntu 6.10 ( I had that disc on hand). I can not get it to connect to my wireless network and was wondering if I could get some help. I have a Broadcom 40100 wireless g card (part of an Athalon 64 Mobile processor).  Thank you in advance for any help!

---

### Post by bmartin on 2007-08-14
According to [this page]("http://gentoo-wiki.com/HARDWARE_Gateway_MX7118"), the relevant line from **lspci**
```
08:07.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```
indicates that you have a Broadcom 4318 chipset. [Here's]("http://ubuntuforums.org/showthread.php?t=405990") a nice installer for it.

P.S. nice HSR reference.

---

### Post by kevindubrow on 2007-08-14
Haha thanks man, Ol' Windows told me the wrong product number. Oh and yeah, Kevin Dubrow...coolest name in the world. My laptop is actually in a Strong Bad messenger bag. :)

---

