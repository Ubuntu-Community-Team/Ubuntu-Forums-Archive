---
title: "network-manager not recognizing intel3945"
date: 2007-12-25
forum: Networking &amp; Wireless
---

### Post by mkimpel on 2007-12-25
I am running Ubuntu Gusty AMD64 on a Dell m90 laptop. I have installed restricted drivers but cannot get my Intel3945 wireless card to be recognized by gnome network-manager or by wicd. I have tried some things recommended on other posts without success. Here is some output demonstrating that the hardware is detected and the appropriate kernel module is loaded and running, but iwlist scan doesn't "see it".

Help??? Thanks, Mark

: sudo lshw -C network
  *-network               
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=ipw3945 latency=0 module=ipw3945
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:18:8b:b6:ee:1d
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.77 duplex=full firmware=5752-v3.19 ip=192.168.1.11 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s

 iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

vmnet1    Interface doesn't support scanning.

vmnet8    Interface doesn't support scanning.

sudo ipw3945d-$(uname -r)
ipw3945d - regulatory daemon
Copyright (C) 2005-2006 Intel Corporation. All rights reserved.
version: 1.7.22
2007-12-25 15:10:49: ERROR: ipw3945d already running.  If ipw3945d is not running then you
need to remove '/var/run/ipw3945d.pid' and try again.

---

### Post by DrIdiot on 2007-12-30
i have this exact same problem.  anyone have solution?

---

### Post by DrIdiot on 2007-12-30
[http://ubuntuforums.org/showthread.php?p=4042303&posted=1#post4042303](http://ubuntuforums.org/showthread.php?p=4042303&posted=1#post4042303)
[http://ubuntuforums.org/showthread.php?t=638182&highlight=ipw3945+logical+name&page=2](http://ubuntuforums.org/showthread.php?t=638182&highlight=ipw3945+logical+name&page=2)


apparently there's a switch on the laptop (a physical switch) that turns the wireless on/off.  on my dell insipron 1420 it is on the front side next to the SD/MMC card slot.

---

