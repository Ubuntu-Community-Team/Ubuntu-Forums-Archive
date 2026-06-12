---
title: "Wired connection not working"
date: 2016-01-25
forum: Networking &amp; Wireless
---

### Post by sharas2 on 2016-01-25
Hi,
I am using Ubuntu 15.10 and encountered some issues with wired connection.
after using grub, using Ubuntu recovery option with networking enabled it messed up my wired connection settings.

ifconfig eth0 up
returns:

eth0: ERROR while getting interface flags: No such device

dmesg | grep eth
returns:

[    2.073397] usbcore: registered new interface driver cdc_ether
[    2.215551] r8152 2-1:1.0 eth0: v1.08.1 (2015/07/28)
[    3.237153] r8152 2-1:1.0 enx9cebe8261253: renamed from eth0
[   69.963790] r8152 2-1:1.0 eth0: v1.08.1 (2015/07/28)
[   71.017553] r8152 2-1:1.0 enx9cebe8261253: renamed from eth0
[  195.797143] r8152 2-1:1.0 eth0: v1.08.1 (2015/07/28)
[  196.861909] r8152 2-1:1.0 enx9cebe8261253: renamed from eth0
[  229.932958] r8152 2-1:1.0 eth0: v1.08.1 (2015/07/28)
[  230.981139] r8152 2-1:1.0 enx9cebe8261253: renamed from eth0



Wireless connection still works fine. I'm using laptop (Asus UX305FA), so my wired connection is though usb to ethernet adapter.
Wired connection worked out of the box with adapter on fresh install.
I would appreciate any help I could get on how to resolve this issue.

---

