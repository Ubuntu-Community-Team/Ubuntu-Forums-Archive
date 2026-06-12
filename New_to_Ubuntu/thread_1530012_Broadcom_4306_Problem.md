---
title: "Broadcom 4306 Problem"
date: 2010-07-13
forum: New to Ubuntu
---

### Post by sjewenp on 2010-07-13
I am new to ubuntu. I can't get my wireless card to work. I have picked my way through the wireless sticky thread and it doesn't work. I've obtained the right drivers (I think) and still no dice. 
After running the recommended commands, I got this:
(I know it says my wireless card is disabled but can't figure out how to enable it)

sara@sara-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:0f:1f:22:c2:7c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.1.102 latency=32 multicast=yes
       resources: irq:11 memory:faffe000-faffffff
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:7 memory:faff6000-faff7fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:96:f2:98:0a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

Thanks for your help. I've been working at this for about three days.

---

