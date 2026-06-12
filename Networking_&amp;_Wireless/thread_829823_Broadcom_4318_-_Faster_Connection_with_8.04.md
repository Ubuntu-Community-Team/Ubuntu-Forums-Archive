---
title: "Broadcom 4318 - Faster Connection with 8.04??"
date: 2008-06-15
forum: Networking &amp; Wireless
---

### Post by whos2know on 2008-06-15
Hi,  

The native Broadcom firmware sucks.  Is there any good post that anyone would recommend or anyone know how to fix this to run faster then it does?  This is my info on my card.

Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

Any help would be great!! Thank you!

Bobby

---

### Post by squeakysystem on 2008-06-15
Are you using ndiswrapper? I have the same card and never managed to get it working that way.

In the end, I used the custom firmware and the b43 driver, and now my card finally works. Not sure about the exact transfer speed, but it seems reasonable.

For details, see this page:

[http://ubuntuforums.org/archive/index.php/t-763995.html](http://ubuntuforums.org/archive/index.php/t-763995.html)

Note: I installed both the wl_apsta-3.130.20.0.o and the wl_apsta_mimo.o firmware (the latter from [http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2)).

HTH

---

### Post by whos2know on 2008-06-16
thank you!! I'll try it out and let you know what happen!  Thanks again!

Bobby

---

