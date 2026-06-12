---
title: "Netgear AC1200 Dual Band Wi-Fi USB 3.0 Adapter (Netgear 6210)"
date: 2016-04-04
forum: Networking &amp; Wireless
---

### Post by Ian_MacLaren on 2016-04-04
The thread: [http://ubuntuforums.org/showthread.php?t=2265150&page=2](http://ubuntuforums.org/showthread.php?t=2265150&page=2) was closed with no proper solution.  

Turns out, with a little digging, that it is possible to run this wifi adapter on Ubuntu.  Details:

Ubuntu 15.10
Driver and instructions: [https://github.com/jurobystricky/Netgear-A6210](https://github.com/jurobystricky/Netgear-A6210)
Hint: after installation, restart the computer totally (not just the network manager, as suggested by jurobystricky).

Performance with us in an upstair bedroom (wireless router downstairs):
Generic n600 omnidirectional dongle: 250 kB/s
AC1200 in right orientation: ~ 2 MB/s

It was worth the hassle of installing it!

Thanks jurobystricky!

All the best

Ian

---

### Post by jeremy31 on 2016-04-04
Please post the info for the device from ```
lsusb
``` as other wifi cards may have the same ID

---

