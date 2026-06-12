---
title: "No Internet on Kubuntu !!"
date: 2008-03-11
forum: Networking &amp; Wireless
---

### Post by KJay on 2008-03-11
I've already spent some days trying to get my wireless connection to work on my laptop with kubuntu, but I'm new to linux so i haven't been able to do it by myself.

I have Kubuntu 6.06 for AMD64 and my wireless card is a Broadcom BCM4318. From what I have read on documents, this card should be supported by ndiswrapper. When i use the *sudo lshw -C network* command, it displays this:
------------------------------------------------------------------------------------------------------------------
*-network
       description: Ethernet interface
       product: 88E8036 Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth0
       version: 10
       serial: 00:e0:b8:8e:f2:30
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=sky2 driverversion=0.15 firmware=N/A link=no multicast=yes port=twisted pair
       resources: iomemory:d0200000-d0203fff ioport:a000-a0ff irq:233
  *-network DISABLED
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@05:02.0
       logical name: eth1
       version: 02
       serial: 00:14:a5:85:23:3b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.15-23-amd64-generic link=no multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:d0304000-d0305fff irq:50
------------------------------------------------------------------------------------------------------------------

 As I said I'm new to linux so I don't even know how to install ndiswrapper. Any help on getting my wireless network working is highly appreciated.

---

### Post by 1010011010 on 2008-03-11
Does your LAN connection work?

---

### Post by KJay on 2008-03-11
I can't get the LAN to work either

---

