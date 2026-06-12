---
title: "Freeze on sudo modprode ndiswrapper"
date: 2007-05-10
forum: Networking &amp; Wireless
---

### Post by timorrill on 2007-05-10
I've just installed Feisty Fawn and downloaded the latest stable release (1.43) of ndiswrapper. The installation seems to go fine, but when I use the command "sudo modprobe ndiswrapper", the terminal freezes. Any suggestions?

---

### Post by chili555 on 2007-05-10
Perhaps there is a native driver that needs to be removed and blacklisted? bcm43xx, maybe?

---

### Post by timorrill on 2007-05-10
How can I find out what needs to be blacklisted, and how do I blacklist it once I find out? Sorry -- Linux noob.

---

### Post by chili555 on 2007-05-10
Please tell us what:```
sudo lshw -C network
```says about the card. If it's pcmcia or USB, be sure it's plugged in (don't be a noob like I once was!) Thanks.

---

### Post by timorrill on 2007-05-10
It only spits out the info for  the Ethernet card:
*-network
   description: Etnernet interface
   product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
   vendor: Broadcom Corporation
   physical id: 0
   bus info: pci@02:00.0
   logical name: eth0
   version: 01
   serial: 00:13:72:c5:7b:14
   capacity: 1GB/s
   width: 64 bits
   clock: 33Mhz
   capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
   configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.72 firmware=5751-v3.44a latency=0 link=no multicast=yes port=twisted pair
   resources: iomemory:fe8f0000-fe8fffff irq:16

---

### Post by chili555 on 2007-05-10
Ugggh! Let's try:```
lspci -vv
```If this also tells us nothing about the card, let's just pull out the adapter and tell me everyting about the manufacturer, model and, most importantly, the version. Wireless adapters often come with multiple chipsets all within the same model.

---

