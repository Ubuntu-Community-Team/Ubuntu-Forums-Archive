---
title: "Netgear WG111v2 issues"
date: 2007-12-11
forum: Networking &amp; Wireless
---

### Post by Huskers on 2007-12-11
I am having a problem setting up my Netgear WG111v2 USB Wireless Adapter. I just did a clean reinstall and am going through the troubleshooting in the Documentation. I was able to detect the USB Adapter and then moved on to checking for a driver. The documentation said to entry this command:

sudo lshw -C network

and this is what it returned:

*-network:0 
description: Ethernet interface 
product: RTL8139 Ethernet 
vendor: D-Link System Inc 
physical id: b 
bus info: pci@0000:01:0b.0 
logical name: eth0 
version: 10 
serial: 00:50:ba:5d:af:10 
size: 10MB/s 
capacity: 100MB/s 
width: 32 bits 
clock: 33MHz 
capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s 
*-network:1 
description: Ethernet interface 
product: RTL8139 Ethernet 
vendor: D-Link System Inc 
physical id: c 
bus info: pci@0000:01:0c.0 
logical name: eth1 
version: 10 
serial: 00:50:ba:5c:48:3f 
size: 10MB/s 
capacity: 100MB/s 
width: 32 bits 
clock: 33MHz 
capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=halfsudo lshw -C network latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s 
*-network DISABLED 
description: Wireless interface 
physical id: 1 
logical name: wlan0 
serial: 00:18:4d:0e:40:30 
capabilities: ethernet physical wireless 
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

The network 0 and network 1 are two D-link PCIs that are in the computer. The “network DISABLED” is, I think, the USB Adapter.

Can someone tell me why it is disabled, and how to correct that. Also, I did this to check for the driver. I do not think it is there, is that correct?

Any help would be greatly appreciated. Thanks.

---

### Post by Huskers on 2007-12-11
Anyone have any thoughts here?](*,)

---

