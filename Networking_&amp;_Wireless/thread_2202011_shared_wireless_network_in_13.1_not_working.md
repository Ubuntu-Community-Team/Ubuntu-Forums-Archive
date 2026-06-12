---
title: "shared wireless network in 13.1 not working"
date: 2014-01-27
forum: Networking &amp; Wireless
---

### Post by Anoop_S_Mahajan on 2014-01-27
Hello,

I want to share internet from my Dell 3400 laptop so that I can connect other devices to the internet. I tried to create a wireless network using the normal procedure through the network connections and it creates it successfully. However, there is no internet being shared. Any idea what could be wrong? My hardware details are below.


lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: QCA9565 / AR9565 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 01
       serial: 34:23:87:b4:22:c7
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.11.0-15-generic firmware=N/A ip=10.42.0.33 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:f7900000-f797ffff memory:f7980000-f798ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 10
       serial: e0:db:55:bd:32:29
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.037.00-NAPI duplex=half latency=0 link=no multicast=yes port=twisted pair speed=10Mbit/s
       resources: irq:57 ioport:e000(size=256) memory:f7804000-f7804fff memory:f7800000-f7803fff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

---

### Post by Anoop_S_Mahajan on 2014-01-28
Just in case someone else faces this issue:
I tried making the connection manually in edit connections of through create a new wireless connection. I also chose WEP key instead of WEP pass phrase and it works well. I have no idea why, but it works.
Anoop

---

