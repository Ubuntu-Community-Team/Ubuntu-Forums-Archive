---
title: "Help getting wireless internet"
date: 2008-07-27
forum: Networking &amp; Wireless
---

### Post by papsynot on 2008-07-27
Hello!
I just installed Ubuntu and I'm having trouble connecting to my wireless internet. When I type lshw -C network into the terminal I get:

*-network:0
	description: Ethernet Interface
	product: SiS900 PCI Fast Ethernet
	vendor: Silicon Integrated Systems
	physical id: 3
	bus info: pci@0000:00:03.0
	logical name: eth0
	version: 90
	serial: 00:07:95:32:d4:4d
	width: 32 bits
	clock: 33MHz
	capabilities: bus_master cap_list ethernet physical
	configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr 2 2006 latency=64 maxlatency=11 mingnt=52 module=sis900 multicast=yes
*-network:1
	description: Network Controller
	product: BCM4303 802.11b Wireless LAN Controller
	vendor: Broadband Corporation
	physical id: b
	bus info: pci@0000:00:0b.0
	version: 02
	width: 32 bits
	clock: 33MHz
	capabilities: bus_master cap_list
	configuration: driver=b43-pci-bridge latency=64 module=ssb
*-network:DISABLED
	description: Wireless Interface
	physical id: 1
	logical name: wlan0
	serial: 00:06:25:12:a7:d9
	capabilities: ethernet physical wireless
	configuration: broadcast=yes multicast=yes wireless=IEEEE 802.11b

I don't know what else to do from here.
Please help! Thanks

---

### Post by papsynot on 2008-07-27
Also as a side note I have no wired connection, so I can't do anything that requires that.

---

### Post by superprash2003 on 2008-07-28
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by Kevbert on 2008-07-28
Please see this [post]("http://ubuntuforums.org/showpost.php?p=5469730&postcount=13").  This works for Hardy Heron and Intrepid Ibex.

---

### Post by papsynot on 2008-07-28
That one fixed it, thanks for the help!

---

