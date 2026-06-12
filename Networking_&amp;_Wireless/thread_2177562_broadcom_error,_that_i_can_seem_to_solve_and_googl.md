---
title: "broadcom error, that i can seem to solve and google has no answer"
date: 2013-09-29
forum: Networking &amp; Wireless
---

### Post by merte-edenflower on 2013-09-29
look at this:

root@tom-laptop:/home/tom# dmesg | grep b43 
[   39.484161] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   39.528015] b43-phy0 ERROR: FOUND UNSUPPORTED PHY (Analog 15, Type 15 (UNKNOWN), Revision 255)
[   39.528035] b43: probe of ssb0:0 failed with error -95
[  355.754946] b43-phy1: Broadcom 4318 WLAN found (core revision 9)
[  355.800054] b43-phy1 ERROR: FOUND UNSUPPORTED PHY (Analog 15, Type 15 (UNKNOWN), Revision 255)
[  355.800099] b43: probe of ssb0:0 failed with error -95

the module is loaded, but it is having trouble with starting it it seems...

anyone got any ideas?

---

### Post by Hadaka on 2013-09-29
Hi,from a wired connection  please do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe b43
```
thanks.

---

