---
title: "WLAN driver missing??"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by nene7 on 2010-05-05
hi i have a dell inspiron 6400, and i install opensolaris 2009.06 snv_111b X86 but missing the wireless lan driver and i tried to connect from eternet but dont connect. The driver are missing:
- Broadcom Corporation BCM4311 802.11b/g WLAN
- Broadcom Corporation BCM4401-B0 100Base-TX
 how i can find and install, it previously have ubuntu and work well but i dont know how find to opensolaris??

---

### Post by bredman on 2010-05-06
The BCM43xx firmware is not included in most free operating systems because of legal issues, but they are freely available to download and safe to use.

Search the internet for b43-cutter for your operating system. This is the official firmware installer for the BCM43xx hardware.

---

### Post by kwacka on 2010-05-06
If you connect by wire to a router, it will automatically set up with 'restricted drivers'.

just need to add security, etc.

---

### Post by 3rdalbum on 2010-05-06
You'd probably be better off asking on an OpenSolaris forum, but with Solaris they have a stable kernel ABI, so you just find a Solaris driver for your card online and follow the instructions to install it.

I don't know much about Solaris; maybe the driver is included but the firmware isn't. Best to ask somewhere else, I think.

---

