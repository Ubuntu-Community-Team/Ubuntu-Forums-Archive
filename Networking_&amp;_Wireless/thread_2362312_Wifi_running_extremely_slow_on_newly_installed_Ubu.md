---
title: "Wifi running extremely slow on newly installed Ubuntu"
date: 2017-05-26
forum: Networking &amp; Wireless
---

### Post by acatius on 2017-05-26
Hello, 
I could not find solution for my problem in the existing threads, so here is my problem:
I have a Dell Latitude E6400 and I just installed Ubuntu 16.04, and wifi runs extremely slow on my computer, but it was ok when I had windows on it.

here is some output from running sudo lshw -C network:


 *-network
       description: Network controller
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f1ffc000-f1ffffff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:23:4d:b3:4d:ba
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=4.8.0-52-generic firmware=666.2 ip=192.168.1.104 link=yes multicast=yes wireless=IEEE 802.11

---

