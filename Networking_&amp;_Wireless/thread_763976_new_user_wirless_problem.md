---
title: "new user wirless problem"
date: 2008-04-23
forum: Networking &amp; Wireless
---

### Post by Bad Boy Bubby on 2008-04-23
It seems to have detected and setup my card but says its disabled for wireless :/

simon@simon-laptop:~$ sudo lshw -C network
[sudo] password for simon: 
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:0b:02.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:85:0c:ec
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:0b:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:af:af:c3
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

at the third network section it says disabled how do i enable this ?

it is a broadcom 4306 card i think

thanks

---

### Post by Bad Boy Bubby on 2008-04-24
hehe i got it working

i had to conenct to the internet using another wireless card i had and install the b43-fwcutter package this had not been installed originally, i think it should have been.  

It installed and configured all now working ok

the only thing i think may be wrong is the card speed 11b instead of 11g but I will look into this later

:guitar:

thanks to me :D

---

