---
title: "Enabling Wireless"
date: 2008-07-24
forum: Networking &amp; Wireless
---

### Post by noimus on 2008-07-24
This is what i get in the terminal after typing 

```
lshw -C network
```

> *-network:0
description: Ethernet interface
product: RTL-8139/8139C/8139C+
vendor: Realtek Semiconductor Co., Ltd.
physical id: 1
bus info: pci@0000:06:01.0
logical name: eth0
version: 10
serial: 00:16:d4:15:e6:23
size: 100MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.81 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s

[B]
BUT I DONT GET[/B] Could it be because i didnt install Ubuntu yet? How do i get wireless up and running?


*-network:1 DISABLED
description: Wireless interface
product: AR2413 802.11bg NIC
vendor: Atheros Communications Inc.
physical id: 2
bus info: pci@0000:06:02.0
logical name: wifi0
version: 01
serial: 00:16:ce:8a:89:c9
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list logical ethernet physical wireless
configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11b
[SIZE="4"][B][U]
How do i get wireless up and running?[/U][/B][/SIZE]

---

### Post by noimus on 2008-07-24
Seriously come on guys i really like Linux. I wanna delete Vista and keep Ubuntu 8.04

---

### Post by MrSootentai on 2008-07-24
We need some more info first of all.
Secondly, did u check the stickied topics?? Or search the forums for your specific problem?

---

### Post by powerpleb on 2008-07-24
> **noimus said:**
> Seriously come on guys i really like Linux. I wanna delete Vista and keep Ubuntu 8.04

Post the output of this:
```
lspci
lsusb
```

These commands give you a list of your PCI and USB hardware. Look for your wireless device in the list. 

Sometimes Ubuntu tries to install drivers that do not work with a wireless device (this happened to me with an Atheros wireless device). So you will need to search for a manual way to get them working.

Ndiswrapper is a not so preferable alternative. It used the Windows drivers of your device.

---

