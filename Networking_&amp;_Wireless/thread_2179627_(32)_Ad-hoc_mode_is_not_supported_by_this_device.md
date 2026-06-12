---
title: "(32) Ad-hoc mode is not supported by this device"
date: 2013-10-09
forum: Networking &amp; Wireless
---

### Post by gbooty on 2013-10-09
I'm trying to connect my android phone and ubuntu laptop. I get "(32) Ad-hoc mode is not supported by this device"

I found this bug discussion [https://bugs.launchpad.net/ubuntu-nexus7/+bug/1077704](https://bugs.launchpad.net/ubuntu-nexus7/+bug/1077704)

I'm not 100% sure the problem I am experiencing is a driver issue, or the bug they are specifically discussing. If my problem is the same, their solution is to patch the kernel with this [https://launchpadlibrarian.net/132034143/linux-nexus7_3.1.10-9.27-adhoc.patch](https://launchpadlibrarian.net/132034143/linux-nexus7_3.1.10-9.27-adhoc.patch)

Kernel patching seems as hard as reinventing the wheel. I'm probably  just too tired right now and will try some more tomorrow. Any guidance though would  be greatly appreciated.

---

### Post by gbooty on 2013-10-09
Needed some fresh eyes. 

It was my BCM4313 driver. This driver is sooooo awful, came with my laptops, has caused lots of problems whenever I tried to do anything unique.

This command to check your exact version
lspci -vvnn | grep 14e4

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

I then used this driver

[wl]("http://www.broadcom.com/support/802.11/linux_sta.php") - Proprietary Broadcom STA Wireless driver  
For Chip ID BCM4311, BCM4312, BCM4313, BCM4321, BCM4322, BCM43224, BCM43225, BCM43227 and BCM43228.


Then followed this readme
[http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)


SOLVED

---

