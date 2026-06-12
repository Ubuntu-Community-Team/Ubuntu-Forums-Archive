---
title: "wireless wont startup in gutsy"
date: 2007-12-14
forum: Networking &amp; Wireless
---

### Post by shyamsg on 2007-12-14
HI,
I just installed Gutsy on my HP laptop. I also replaced nm with wicd. Both of them just wont find any wireless networks. I then figured out that my wireless interface is disabled. How do I make it enabled at startup? 
Here is the output from my lshw -C network

  *-network DISABLED      
       description: Wireless interface
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth1
       version: 01
       serial: 00:1a:73:38:73:51
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=0 link=no module=bcm43xx multicast=yes wireless=IEEE 802.11b/g


TIA
Shyam

---

