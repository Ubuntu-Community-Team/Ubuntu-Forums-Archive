---
title: "Laptop with Broadcom BCM4306 wireless connection issue."
date: 2007-06-12
forum: Networking &amp; Wireless
---

### Post by samhakim on 2007-06-12
New Guy here says Hello! 

My laptop can connect with a wire connection, but the wireless part is a real challenge.  

In terminal this is the info I get:
 *-network:0 DISABLED
             description: Wireless interface
             product: BCM4306 802.11b/g Wireless LAN Controller
             vendor: Broadcom Corporation
             physical id: 9
             bus info: pci@00:09.0
             logical name: eth1
             version: 03
             serial: 00:0b:6b:48:65:df
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master ethernet physical wireless
             configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-16-generic latency=64 multicast=yes wireless=IEEE 802.11b/g
             resources: iomemory:d0004000-d0005fff irq:1

Can anyone help me activate the wireless if possible.

Many Thanks,
Sam

---

### Post by wsx123 on 2007-06-12
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported), Try this link.
I use a Belkin card that shows up as Broadcom 4306. I used the standard bcm43xx driver and had to install it using fw-cutter. I'm very new to linux (3 days) but I will try to answer questions.

---

