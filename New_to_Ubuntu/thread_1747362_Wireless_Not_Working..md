---
title: "Wireless Not Working."
date: 2011-05-02
forum: New to Ubuntu
---

### Post by archxeon on 2011-05-02
Hi all,

I have tried lots of things from all these forums and yet I cannot get the wireless to work. I installed Ubuntu 11 today and that was the easy part. I have been stuck trying to get the wireless work ever since. Ethernet works, but wireless doesn't. I have Broadcom 4311. 

Some of things that I have tried includes : 
b43-fwcutter

etc.

Also, when I go to the Additional Hardware the driver seems to be active and is shown but I cannot connect at all.

Somethings that might help you guys to answer this question:

0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at fe8fc000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: b43-pci-bridge
    Kernel modules: wl, ssb

yum install b43-fwcutter wget
Setting up Install Process
No package b43-fwcutter available.
No package wget available.
Nothing to do

---

### Post by mörgæs on 2011-05-02
Hi, welcome to the fora.

Try searching here:
[http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)
especially the sticky notes.

---

