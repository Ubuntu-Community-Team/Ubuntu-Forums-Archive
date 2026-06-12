---
title: "Having trouble with my wifi adapter"
date: 2018-08-08
forum: Networking &amp; Wireless
---

### Post by xforce0 on 2018-08-08
My Netgear A6200 v2 wireless adapter is detectable on my PC, however, when I try configuring it in the Netgear wireless adapter wizard via wine, I get an error saying "No wireless adapter detected".

Results from ```
Lsub
uname -r
```:

```
xforce@pcg27:~$ lsusb
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 003: ID 0665:6000 Cypress Semiconductor 
Bus 005 Device 002: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 05dc:a81d Lexar Media, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0846:9050 NetGear, Inc. A6200 802.11a/b/g/n/ac Wireless Adapter [Broadcom BCM43526]
Bus 001 Device 003: ID 0a5c:21e8 Broadcom Corp. BCM20702A0 Bluetooth 4.0
Bus 001 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
xforce@pcg27:~$ uname -r
4.15.0-30-generic
xforce@pcg27:~$ 


```

---

### Post by wildmanne39 on 2018-08-08
*Thread moved to **Networking & Wireless for a more appropriate fit**.*

---

### Post by chili555 on 2018-08-08
> 0846:9050 NetGear, Inc. A6200 802.11a/b/g/n/ac Wireless Adapter [Broadcom BCM43526]A Google search for the usb.id for your device, 0846:9050, returns this: [https://wikidevi.com/wiki/Netgear_A6200](https://wikidevi.com/wiki/Netgear_A6200)

> Probable Linux driver: NoneGoogle also returns many references to ndiswrapper, the mechanism to use Windows XP driver files to drive the device in Linux.

Even if you have the XP files, not 7 or 8 or 10 or otherwise, ndiswrapper is a bit obsolete. I haven't seen it work properly in a few years now.

I have only said this about 3-4 devices in my career here, but this device will probably never work. I'd get a different fully-supported device. Some kind soul created a sticky on that very subject: [https://ubuntuforums.org/showthread.php?t=2397914](https://ubuntuforums.org/showthread.php?t=2397914)

---

### Post by xforce0 on 2018-08-08
Thanks for helping me troubleshoot.

---

