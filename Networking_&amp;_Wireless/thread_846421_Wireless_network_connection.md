---
title: "Wireless network connection"
date: 2008-07-01
forum: Networking &amp; Wireless
---

### Post by dimitry781 on 2008-07-01
Help!!!! [-o<

I've installed Ubuntu 8.04 yesterday from Windows XP (-> Wubi). Though I cannot connect my laptop to wireless network. :( On Windwos everything works perfectly! I cannot connect my laptop to the Internet via wire, only wirelessly. I installed Wicd, but it does not list any wireless networks. I run the following command
```
lshw -C network
```

and that's what I got:
```
*-network:0 DISABLED
	description: Ethernet interface
	product: RTL-8139/8139C/8139C+
	vendor: Realtek Semiconductor Co., Ltd.
	physical id: 0
	bus info: pci@0000:05:00.0
	logical name: eth0
	version: 10
	serial: 00:c0:9f:df:e9:f2
	width: 32 bits
	clock: 33MHz
	capabilities: bus_master cap_list ethernet physical
	configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
*-network:1
	description: Network controller
	product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
	vendor: Broadcom Corporation
	physical id: 2
	bus info: pci@0000:05:02.0
	version: 02
	width: 32 bits
	clock: 33MHz
	capabilities: bus_master
	configuration: driver=b43-pci-bridge latency=64 module=ssb
*-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:a5:28:49:0b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

```

As I am A complete newbie to Linux, information above does not make a lot of sense to me. I do not know what the problem is and how to fix it? :confused:

---

### Post by nobbydog on 2008-07-01
hi dimitry
Ihave the same problen download via wubi into vista windows ok cannot connect to wireless on ubuntu i hope someone can help us.
i am a newbie.
nobbydog

---

### Post by superprash2003 on 2008-07-01
please post your iwconfig output

---

