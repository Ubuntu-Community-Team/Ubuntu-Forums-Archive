---
title: "Ralink RT2870 driver on Ubuntu 15.10"
date: 2016-05-11
forum: Networking &amp; Wireless
---

### Post by leon36 on 2016-05-11
Hi, i have a similar problem, but when i type:
dmesg | grep 7601

I get:
[    1.703661] usb 1-3: New USB device found, idVendor=148f, idProduct=7601
[   19.416303] mt7601Usta: disagrees about version of symbol module_layout

so I don't know what to do :(
the 'modprobe' commands don't work

---

### Post by chili555 on 2016-05-11
There are so many unknowns here. You obviously didn't compile the driver from the posts above; it is not mt7601Usta, it is mt7601u. You aren't running 16.04, although you should be, as the driver is present by default.

Did you try the driver above?

Please provide the details as described here: [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by slickymaster on 2016-05-12
Moved to a thread of its own.

Please don't hijack other people's threads. Not only it dilutes community effort but it's also the wrong way to get the proper and adequate help to your problem.

---

