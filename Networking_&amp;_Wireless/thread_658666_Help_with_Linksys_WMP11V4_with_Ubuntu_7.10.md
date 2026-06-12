---
title: "Help with Linksys WMP11V4 with Ubuntu 7.10"
date: 2008-01-04
forum: Networking &amp; Wireless
---

### Post by robfindlay on 2008-01-04
I've been running 7.10 for a month or two and have just added a wireless card, I can't figure out how to configure it or how to get it working. 

Relevant portion of LSPCI

00:0a.0 Ethernet controller: Linksys, A Division of Cisco Systems WMP11v4 802.11b PCI card

Relevant portion of lshw: 

*-network:0 UNCLAIMED   
       description: Ethernet controller
       product: WMP11v4 802.11b PCI card
       vendor: Linksys, A Division of Cisco Systems
       physical id: a
       bus info: pci@0000:00:0a.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 maxlatency=32 mingnt=32
  *-network:1
       description: Ethernet interface
       product: NC100 Network Everywhere Fast Ethernet 10/100
       vendor: ADMtek
       physical id: c
       bus info: pci@0000:00:0c.0
       logical name: eth0
       version: 11
       serial: 00:04:5a:69:53:06
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.15 ip=192.168.1.104 latency=32 maxlatency=255 mingnt=255 module=tulip multicast=yes


If someone could point me in the direction of a how-to for this, or give me something to get started I'd much appricate it.

-R

---

### Post by robfindlay on 2008-01-05
bumb

---

