---
title: "gusty-&gt;hardy-&gt;gutsy no wireles no ethernet HELP"
date: 2008-07-07
forum: Networking &amp; Wireless
---

### Post by gleble on 2008-07-07
I used to have gutsy but updated to hardy. Found I had no wireless or ethernet. After two days searching foruums I was still stuc so I reinstalled gutsy. Still no wireless or ethernet. I am running an Acer Aspire 3680. 
This is the result of lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:16:36:c8:83:b9
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.18 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network DISABLED
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:0a:03.0
       logical name: eth1
       version: 02
       serial: 00:19:7d:34:6b:2e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=64 module=bcm43xx multicast=yes wireless=IEEE 802.11b/g
I've been at this for days . Can someone PLEASE help?

---

