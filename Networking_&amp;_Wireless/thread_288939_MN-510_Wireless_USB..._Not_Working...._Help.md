---
title: "MN-510 Wireless USB... Not Working.... Help"
date: 2006-10-30
forum: Networking &amp; Wireless
---

### Post by twalsh2006 on 2006-10-30
Hello,

I need a bit of guidance.  I have installed Ubuntu 6.10 and am trying to get my Microsoft MN-510 USB wireless adapter to function.

The "Networking" tab... shows the adpater as "Wired Connection (wlan0)

The "Device Manager" shows the MN-510 as a USB device and seems to report it correctly.

"lshw" shows: 
*-network DISABLED
description: Ethernet interface
physical id: 1
logical name: wlan0
capabilities: ethernet physical
configuration: broadcast=yes multicast=yes

"lsusb" shows the device correctly

I have added the correct lines to /etc/network/interfaces.

I don't know what to do from here... can someone please give me some guidance?

---

