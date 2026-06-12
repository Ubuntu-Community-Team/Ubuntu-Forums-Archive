---
title: "ndiswrapper - need help with drivers for my card (BCM4318)"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by Hork on 2008-12-21
I was looking in the Wiki and it told me to look at the ndiswrapper list to get drivers for my card but the list won't seem to load.
Here's what lspci lists my card as:
02:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

When could I find the drivers for it?  Thanks

---

### Post by mikeyphi on 2008-12-21
Have you tried the 'official' instructions here:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Hardy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Hardy)

---

### Post by arckeda on 2008-12-21
Perhaps this can help:
[http://ubuntuforums.org/showthread.php?t=285809]("http://ubuntuforums.org/showthread.php?t=285809")

---

### Post by RaZoR1394 on 2008-12-21
> **Hork said:**
> I was looking in the Wiki and it told me to look at the ndiswrapper list to get drivers for my card but the list won't seem to load.
Here's what lspci lists my card as:
02:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

When could I find the drivers for it?  Thanks

Then that wiki is wrong or you've misinterpreted it. b43 works very good for that device and all you need to do is enable firmware in Hardware drivers.

ndiswrapper should be used as a last resort.

---

