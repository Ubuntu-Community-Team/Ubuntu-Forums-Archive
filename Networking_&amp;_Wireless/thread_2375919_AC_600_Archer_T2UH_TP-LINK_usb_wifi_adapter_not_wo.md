---
title: "AC 600 Archer T2UH TP-LINK usb wifi adapter not working"
date: 2017-10-28
forum: Networking &amp; Wireless
---

### Post by rubinglen-b on 2017-10-28
I was just helped on this forum getting a netgear wifi adapter working, but I have one other adapter I would like to get working as well especially since it is dual band.  The device as stated above is a AC 600 Archer T2UH TP-LINK.  

When I plug it in and type lsusb it comes up as: **Bus 001 Device 004: ID 148f:761a Ralink Technology, Corp. **

I looked over the output of dmesg as well but didn't see anything obvious.  Not sure what the driver should be or if it's even available.  thanks for any help!

---

### Post by chili555 on 2017-10-28
Please see my post #18 here: [https://ubuntuforums.org/showthread.php?t=2367163&highlight=mt7610u](https://ubuntuforums.org/showthread.php?t=2367163&highlight=mt7610u)

Sorry.

---

### Post by rubinglen-b on 2017-10-28
thanks for passing along the info.  Maybe I will have luck getting it to work on my little slacko puppy system. cheers!

---

### Post by IwU650vZOTyE on 2018-10-01
Thanks to Hans Ulli Kroll's githubrepo: [https://github.com/ulli-kroll/mt7610u](https://github.com/ulli-kroll/mt7610u), this driver immediately works for the "T2UH AC600" USB dongle (ID 148f: 761a Ralink Technology, Corp.) with the current kernel version (4.15) from Ubuntu 18.04 bionic

---

