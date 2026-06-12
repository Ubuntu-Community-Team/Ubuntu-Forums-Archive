---
title: "Wireless not working properly"
date: 2008-05-10
forum: Networking &amp; Wireless
---

### Post by neptuneg on 2008-05-10
Hi guys,

I have a Linksys WMP54G (ver 1) PCI wireless card that I cannot get to work correctly.  I have installed ndiswrapper and executed the proper commands, but it seems that the b43 driver is still being used for the card.  I also do not have any hardware listed in my hardware manager.  Here is the output of:

lshw -C network:

*-network:0
description: Network controller
product: BCM4306 802.11b/g Wireless LAN Controller
vendor: Broadcom Corporation
physical id: 1
bus info: pci@0000:01:01.0
version: 02
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list
configuration: driver=b43-pci-bridge latency=32 module=ssb
*-network: DISABLED
description: Wireless interface
physical id: 1
logical name: wlan0
serial: 00:0c:41:12:ab:94
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

output of lspci:

01:01.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)

Any ideas on how to make the wireless work correctly?

---

### Post by neptuneg on 2008-05-10
anyone?

---

### Post by neptuneg on 2008-05-11
I've found that the drive is apparently assigned to the device, using ndiswrapper -a.  But, the light on the device will not light up and it will not connect to any wireless network.

---

