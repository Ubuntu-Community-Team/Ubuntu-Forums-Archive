---
title: "internal wireless card"
date: 2007-06-15
forum: Networking &amp; Wireless
---

### Post by mr.farenheit on 2007-06-15
i do i configure kwifi to read my internal wireless card instead of scanning for one in my pcmcia slot?

---

### Post by kevdog on 2007-06-15
What is the result of:

lshw -C network

---

### Post by mr.farenheit on 2007-06-19
WARNING: you should run this program as super-user.
  *-network:0
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@06:01.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:1d:a3:6a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too ip=192.168.1.4 multicast=yes
       resources: ioport:a000-a0ff iomemory:c0202000-c02020ff irq:225
  *-network:1 DISABLED
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@06:02.0
       logical name: eth1
       version: 02
       serial: 00:16:cf:6b:f5:1b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:c0200000-c0201fff irq:233

this is what i get

---

