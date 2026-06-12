---
title: "Network Manager switches off Broadcom 43xx automatically"
date: 2007-12-11
forum: Networking &amp; Wireless
---

### Post by reef2dive on 2007-12-11
I have a HPze2000 with built-in broadcom wireless. It has been working fine Kubuntu 6.06 with NDISWRAPPER. Now I am on Ubuntu Gutsy using the native support in Ubuntu. 

The Network manager starts fine but when I connect I can see that the indicator for the switch off and on button of the wlan (BCM43xx) flickers. After some flickering the wireless is off and impossible to switch on without a reboot. (There are no issues to connect to the wireless using windows)

Prior to connection the status is the following
sudo lshw -C network

  *-network:1
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:05:02.0
       logical name: eth1
       version: 02
       serial: 00:14:a5:60:32:52
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=64 link=no module=bcm43xx multicast=yes wireless=IEEE 802.11b/g

As you can see it is on. After trying to connect to the wireless the following is the status

  *-network:1 DISABLED
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:05:02.0
       logical name: eth1
       version: 02
       serial: 00:14:a5:60:32:52
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=64 link=no module=bcm43xx multicast=yes wireless=IEEE 802.11b/g

Does anyone have any tips on how to make the bcm not switch off so the connection  can be finalized??? Which logs I am supposed to look at to understand what actually is happening. Or should I just drop the native support and go for NDISWRAPPER.

---

### Post by reef2dive on 2007-12-26
Consider this closed. Update to later SW level fixed it. No clue of what made it work.

---

