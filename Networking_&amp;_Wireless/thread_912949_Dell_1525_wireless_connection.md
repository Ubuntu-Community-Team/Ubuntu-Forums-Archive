---
title: "Dell 1525 wireless connection"
date: 2008-09-07
forum: Networking &amp; Wireless
---

### Post by bobkate6 on 2008-09-07
I just dual booted Hardy Heron and Vista on my Dell 1525 and surprise surprise no wireless connection.After searching for solutions and having limited Ubuntu skills I removed the HD from my Inspiron 6000 which had no problems connecting and connected it via USB to my 1525.Surprisingly to me it connected to the internet with no tweaks.Running lshw -C network
on my dual boot 1525 gave me this




*-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 01
       serial: 00:22:69:5c:9e:9e
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes



The same command while using the USB gave me this 

*-network 
       description: Wireless interface 
       product: BCM4312 802.11b/g 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:0b:00.0 
       logical name: eth3 
       version: 01 
       serial: 00:22:69:5c:9e:9e 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=wl ip=192.168.0.2 latency=0 module=wl multicast=yes wireless=IEEE 802.11 


Two Questions, would the difference in the logical name line be causing 
my problem and is there a way to find out why the USB hardy works and the Dual boot doesn't.

---

