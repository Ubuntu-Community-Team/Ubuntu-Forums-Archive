---
title: "Wired and Wireless side by side"
date: 2008-07-04
forum: Networking &amp; Wireless
---

### Post by adriaanvk on 2008-07-04
hi,

In the past it was possible to have wired network and wireless network adapter both running. Now i am having Hardy Heron, where there can only be one interface running. If u are on wireless and u plug in a wired network cable, the eth1 adapter is disapearing! an ifconfig eth1 up gives:
eth1: ERROR while getting interface flags: No such device

How can i fix this in Hardy Heron? I already tried to kill NetworkManager, but it still doesn't work. Both the iwl3945 and ipwraw driver gives the same problem, so i conclude that it is another setting in ubuntu?

lshw:
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5753M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 21
       serial: 00:16:d4:40:60:c6
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 firmware=5753m-v3.56 ip=xxxxx latency=0 module=tg3 multicast=yes
  *-network
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ipwraw latency=0 module=ipwraw

thx,

Adriaan

---

### Post by sbrbot on 2008-10-04
Both wired and wireless card can work simultaneously. But you can have only one routing gateway meaning you cannot have 2 different simultaneous connection to Internet. For example you can have active wired Internet connection and scan (monitor) wireless networks in the same time.

---

### Post by iponeverything on 2008-10-04
> **sbrbot said:**
> Both wired and wireless card can work simultaneously. But you can have only one routing gateway meaning you cannot have 2 different simultaneous connection to Internet. For example you can have active wired Internet connection and scan (monitor) wireless networks in the same time.

Not necessarily  true. Having a second default route with higher metric than the first can serve as a backup..

Adriaan -- What is that your trying to do? There are no issues with having more that one interface up at time... You might have to go to manual configuration.

---

