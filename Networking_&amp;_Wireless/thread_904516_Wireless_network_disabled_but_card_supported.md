---
title: "Wireless network disabled but card supported?"
date: 2008-08-29
forum: Networking &amp; Wireless
---

### Post by tupacloveskittens on 2008-08-29
Hi Im really new to ubuntu,
and I cant connect to my wireless network
I think my card is supported but, im not so savvy 
When I type in the command > sudo lshw -C network
I get this
> *-Network
Description: Network controller
product: BCM94311MCG
Vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:03:00.0
Version: 01
Width: 32 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list
configuration: driver=b43-pci-bridge latency=0 module=ssb
      *-Network
description: Ethernet interface
product: PRO/100 VE Network Connection
vendor: Intel Corporation
physical id: 8
bus info: pci@0000:04:08.0
logical name: eth0
version: 02
serial: 00:e0:b8:c0:0b:b2
size: 10MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=57 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
*-network DISABLED
description: wireless interface
physical id: 2
logical name: wlan0
serial: 00:1a:73:2d:13:1a
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g


I hope I provided enough Information

---

### Post by sureshuoh on 2009-02-08
Hi,

By the way did you got answer for your questions?
I am also having the similar problem.
Can you please help me how to proceed!
regards,

---

