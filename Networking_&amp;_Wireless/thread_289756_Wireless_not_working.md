---
title: "Wireless not working"
date: 2006-10-31
forum: Networking &amp; Wireless
---

### Post by twalsh2006 on 2006-10-31
Hello,

I need a bit of guidance. I have installed Ubuntu 6.10 Edgy and am trying to get my Microsoft MN-510 USB wireless adapter to function.

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

### Post by x64Jimbo on 2006-10-31
what happens when you run iwconfig?

---

### Post by twalsh2006 on 2006-10-31
When I run iwconfig the message for wlan0 is: no wireless extensions...

I believe the MN510 is one of the supported wireless USB adapters so why is it so difficult to get working?

Any advice would be appreciated...

---

### Post by x64Jimbo on 2006-10-31
You might try the solutions listed in this thread:
[http://www.ubuntuforums.org/archive/index.php/t-106700.html](http://www.ubuntuforums.org/archive/index.php/t-106700.html)

---

