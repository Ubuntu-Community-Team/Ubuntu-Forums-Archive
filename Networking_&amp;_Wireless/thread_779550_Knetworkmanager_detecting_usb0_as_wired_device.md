---
title: "Knetworkmanager detecting usb0 as wired device"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by pvanos on 2008-05-02
I have hardy with Knetworkmanager detecting usb0 as a wired device, and putting it as default. Maybe due to physical id=1 ?
It should take eth0.
After every restart I have to manually select eth0 instead of usb0. 

Where can I configure Knetworkmanager not to detect usb0 ?
When I try Knetworkmanager's "Manual Configuration", it only shows devices eth0 and eth1.

Output of **sudo lshw -C network** :

*-network:0
       description: Ethernet interface
       product: 82557/8/9/0/1 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: 7
       bus info: pci@0000:00:07.0
       logical name: eth0
       version: 05
       serial: 00:04:ac:c5:77:e1
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=192.168.1.102 latency=64 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 8
       bus info: pci@0000:00:08.0
       logical name: eth1
       version: 42
       serial: 00:50:ba:f0:c6:a2
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=64 link=no maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=10MB/s
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: usb0
       serial: 26:93:e6:7d:96:61
       capabilities: ethernet physical
       configuration: broadcast=yes driver=gl620a driverversion=22-Aug-2005 firmware=Genesys GeneLink link=yes multicast=yes

---

