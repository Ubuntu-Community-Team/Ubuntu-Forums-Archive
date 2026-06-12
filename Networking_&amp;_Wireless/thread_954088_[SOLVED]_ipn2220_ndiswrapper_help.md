---
title: "[SOLVED] ipn2220 ndiswrapper help"
date: 2008-10-20
forum: Networking &amp; Wireless
---

### Post by super.rad on 2008-10-20
Installed ubuntu (intrepid beta) on an old laptop which has an inprocomm ipn2220 wireless card, lspci shows:
```
02:04.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
```
I've read around the forums and realised there is no linux driver so installed ndiswrapper and the windows driver for the card.
All seems to have worked, ndiswrapper -l gives:
```
neti2220 : driver installed
    device (17FE:2220) present
```
but it still isnt showing up in ifconfig or iwconfig. lshw -C network shows:
```
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:af:7d:78
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.2.4 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
       vendor: Linksys, A Division of Cisco Systems
       physical id: 4
       bus info: pci@0000:02:04.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=64 maxlatency=32 mingnt=32
```
so the card is being detected and ndiswrapper shows the driver was installed fine but ubuntu hasn't given it a logical name.
Does anyone know how I can sort this out and get the wireless working? Thanks

---

### Post by super.rad on 2008-10-20
Solved, checked dmesg and turned out I was trying to use 64bit drivers on 32bit ubuntu. Found the right drivers and its working fine

---

