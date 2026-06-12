---
title: "no wlan0 device under linux-2.6.10-5-386
inux-2.6.10-5-k7"
date: 2005-07-17
forum: Networking &amp; Wireless
---

### Post by ShanJi on 2005-07-17
Since I have an Athlon, I wanted to change from i386 to k7 per image package, BUT once I boot k7 my wlan0 device isn't listed anymore (but it shows in lspci). Even if I load the acx_pci module (which definitely is the right module) manually it doesn't show.

Everthing works fine with the i386 kernel.

(iwconfig doesn't list the device)

CARD: D-Link dwl-520+ (i think :)

thanks for reply,

ShanJi

---

### Post by ShanJi on 2005-07-18
If anyone is interested: the firmware in the hotplug folder had a kernel related ending i had to change.

works fine now.

---

### Post by bladesE on 2005-07-18
hi
what changes did you make

---

