---
title: "Unable to connect to wireless network"
date: 2008-09-22
forum: Networking &amp; Wireless
---

### Post by albanach on 2008-09-22
I have a Packard Bell Easynote laptop and I cannot connect to the wireless network.  I have posted the output from lshw -C network command. 

I don't think I'm too far away and must be missing something obvious.
When I try to manually configure the wireless network, nothing happens.

Thank you. 


 *-network:0 DISABLED    
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 6
       bus info: pci@0000:00:06.0
       logical name: wmaster0
       version: 00
       serial: 00:10:60:62:af:6e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci latency=64 module=rt61pci multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:40:d0:93:e2:81
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 ip=192.168.1.101 latency=128 maxlatency=8 mingnt=3 module=via_rhine multicast=yes

---

### Post by superprash2003 on 2008-09-22
[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61)

---

### Post by albanach on 2008-09-23
Thank you.  I will check the site suggested.

---

