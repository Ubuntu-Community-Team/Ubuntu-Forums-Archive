---
title: "Using a Dell VOSTRO and having WiFi problems"
date: 2015-03-24
forum: Networking &amp; Wireless
---

### Post by highillumi on 2015-03-24
I have been a Windows user for a long time now. I would say since about  Windows 95. This is my first time using Linux. I first started with Kali  Linux and found it very difficult to use. I heard that Ubuntu made it  easier to work witth Linux. So my problem is that I installed 14.10 on  my Dell VOSTRO and it seems that after being on for about 20-30 min the  WiFi disconnects itself. Please help would be very greatfull. Not sure  what to type in terminal to fix this or where to find the info to do so.

---

### Post by papibe on 2015-03-24
Hi highillumi. Welcome to the forum ):P

Could you open a terminal, run this commands, and post back the output (you can copy/paste the text)?
```
lspci -nnk | grep -iA2 net

lshw -C network
```
Regards.

---

### Post by highillumi on 2015-03-24
Thanx for the warm welcome :p

When I put in 
lspci -nnk | grep -iA2 net
this comes up
01:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1030 [Rainbow Peak] [8086:008a] (rev 34)
	Subsystem: Intel Corporation Centrino Wireless-N 1030 BGN [8086:5325]
	Kernel driver in use: iwlwifi
--
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
	Subsystem: Dell Device [1028:04d9]
	Kernel driver in use: r8169

and when i put this 
lshw -C network
this come up
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: Centrino Wireless-N 1030 [Rainbow Peak]
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 34
       serial: 58:91:cf:22:9b:42
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.16.0-33-generic firmware=18.168.6.1 ip=192.168.1.8 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:48 memory:d1600000-d1601fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 06
       serial: 5c:f9:dd:41:b1:e7
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168e-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:46 ioport:3000(size=256) memory:d0404000-d0404fff memory:d0400000-d0403fff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.



thanx again for helping me out

---

