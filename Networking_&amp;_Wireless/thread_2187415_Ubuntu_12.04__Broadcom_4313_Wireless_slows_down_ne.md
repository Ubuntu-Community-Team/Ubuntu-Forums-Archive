---
title: "Ubuntu 12.04 / Broadcom 4313 Wireless slows down network"
date: 2013-11-12
forum: Networking &amp; Wireless
---

### Post by enjean on 2013-11-12
I am having similar problems to those described here: [http://ubuntuforums.org/showthread.php?t=2135692](http://ubuntuforums.org/showthread.php?t=2135692). The wireless and wired connection on my computer are working fine, but it seems like whenever I am connected wirelessly, other devices on the network have their connection speed drop.

 I am a Linux novice and would like to make sure I am doing the right thing before I mess with too many things.

Here are my specs:

Machine: ASUS 1015E-DS03 Laptop

lspci -nn | grep 'Wireless'
```
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
```

sudo lshw -C network
```
*-network               
       description: Wireless interface
       product: BCM4313 802.11bgn Wireless Network Adapter
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: dc:85:de:27:c1:a0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.20.155.1 (r326264) ip=192.168.0.16 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:17 memory:f7d00000-f7d03fff
  *-network
       description: Ethernet interface
       product: AR8162 Fast Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 10
       serial: 74:d0:2b:4c:30:2c
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx firmware=alx latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:f7c00000-f7c3ffff ioport:e000(size=128)
```

Any advice would be greatly appreciated!

---

