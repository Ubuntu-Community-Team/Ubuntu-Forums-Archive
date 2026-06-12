---
title: "[Problem Resolved] 20.04.2 Fresh install No wired connection"
date: 2021-05-21
forum: Networking &amp; Wireless
---

### Post by Panama.Craig on 2021-05-21
Soooo... I decided after years of being away from Linux to finally come back. I've dropped most of my gaming for years now, and really only mine crypto and watch YouTube anymore, so I decided to fresh install Linux! I figured going with an LTS Version would be my best bet, and Lo and Behold.... I fresh install and I can't connect to the internet at all! YAY!!! Please don't make me go back to windows. I have my ethernet cable plugged in and also have a wifi adapter, but neither is recognized when I attempt to get them started. If I go to settings>network then the cable unplugged switch is off and I can't flip it to on.

If I type the following in command line, I get the return...

sudo lshw -C network

*-network
description: Ethernet interface
product: 82579V Gigabit Network connection
Vendor: Intel Corporation
Physical id: 19
Bus info:pci@0000:00:19.0
Logical name: eno1
Version: 06
Serial: 44:8a:5b:2b:2b:Ed
Capacity: 1Gbit/s
Width: 32 bits
Clock: 33MHz
Capabilities: pm msi bus_master cap_list ethernet physical therapy 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd  autonegotiation 
Configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k firmware=0.13-4 latency=0 link=no multicast=yes port=twisted pair resources: irq:34 memory:f3400000-f431ffff memory: f4328000-f4328fff ioport:f040(size=32)

*Edit* Bypassed the Ethernet and ethered to update my wifi drivers. Have internet, but over ethernet still doesn't work. OH WELL! Less wires running through a doorway!

---

### Post by TheFu on 2021-05-24
[https://askubuntu.com/questions/1150811/ethernet-card-works-only-after-soft-reboot-82579v-on-xubuntu-18-04](https://askubuntu.com/questions/1150811/ethernet-card-works-only-after-soft-reboot-82579v-on-xubuntu-18-04)
says there could be a startup timing issue with netplan/networking.  
They suggest running **sudo netplan apply** if the wired network isn't working.

If the system isn't using netplan, it probably uses network-manager, then I don't have a clue.
The post says it is only a problem after a soft reboot, which implies it works fine after a hard reboot. I don't know if any of these things are true, but it has been a common problem for network drivers made by other vendors for a decade. I've not seen or experienced that issue with the e1000e driver on my systems, but I don't have the same NIC either.  

I have a 82574L using driver=e1000e driverversion=3.2.6-k duplex=full ; works perfect.

---

### Post by 440music on 2021-06-01
*-network                  
       description: Ethernet interface 
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: enp2s0 
       version: 11 
       serial: 70:85:c2:02:84:b1 
       size: 1Gbit/s 
       capacity: 1Gbit/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=5.11.0-18-generic duplex=full firmware=rtl8168g-2_0.0.1 02/06/13 ip=192.168.221.30 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s 
       resources: irq:36 ioport:e000(size=256) memory:fe900000-fe900fff memory:d0800000-d0803fff 

I can not install any programs using the Auto Installer
I can reach the internet 
Network setting are not available(network is working) multiple IPs are visible using ip addr but not shown using ifconfig, ifconfig show the network setting with 1 IP

My work station is experiencing similar issues:
I can not get beyond my router, I can ping local network IPs but once I try to go beyond the router I get: can not be reached message.
Ubuntu 21.04

The computer I'm on lost the Network setting after the update that required a reboot
The workstation stopped working last Monday 8 days now

---

