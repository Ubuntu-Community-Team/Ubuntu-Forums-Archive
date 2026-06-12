---
title: "How can I enable the last two networks?"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by Yed Ied on 2009-01-27
#1  
Yed Ied 
5 Cups of Ubuntu

 

Join Date: Jan 2009
Posts: 24  Old problem- new Info, wirless Ubuntu 

--------------------------------------------------------------------------------
Hope I'm doing this right.  I can see the two last networks are DISABLED and believe is what is keeping me from being wireless and no network.  Am I wrong?  If not how do I fix it.
Thanks
Gateway laptop MX6436, command prompt-lshw -c network-
*-network
description: ethernet interface
product: 88E8036 PCI-E fast Ethernet Controller
vendor: Marvell Tech. Group Ltd.
physical id: 0
bus info: pci@oooo:03:00.0
logical name: eth0
version 10
serial: 00:e0:b8:8f:6b:6a
capacity: 100MB/s
width 64 bits
clock: 33MHz
capabilities: pm vpd msi pciexpress bus_master cap_list ethernet
phisical tp 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 module=sky2 multicast=yes port=twisted pair
*-network
description: Network controller
product: BCM4318 [Air Force One 54g] 802.11g Wireless LAN Controller
vendor: Broadcom Corp
physical id: 2
bus info: pci@0000:05:02.0
version:02 
width: 32 bits
clock: 33MHz 
capabilities: bus_master
configuration: driver=b43-pci-bridge latency=64 module=ssb
*-network:1 DISABLED
description: Ethernet Interface
physical id: 2
logical name: pan0
serial: ba:70:fd:f6:86:b3
capabilities ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3
firmware=N/A link=yes multicast=yes
*-network:0 DISABLED
description: Wireless interface
physical id: 1
logical name: wlan0
serial: 00:14:a5:87:f2:3d
capabilities: ethernet physical wireless
configuration: broadcast+yes multicast=yes wireless=IEEE 802.11g
Hope this is what you need.

---

