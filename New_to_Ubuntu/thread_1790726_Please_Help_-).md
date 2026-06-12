---
title: "Please Help :-)"
date: 2011-06-25
forum: New to Ubuntu
---

### Post by Extratus on 2011-06-25
I'd like to know how to connect to the Aut0 thing, wired network, so i can download a package to fix my wireless :P

Help is greatly appreciated :>

---

### Post by wafflesausage on 2011-06-25
Try running dhclient on it. In case you don't have any luck with that, an easier alternative is to plug an ethernet cable into it and hit restart (the purpose of restarting is that it will restart all of your daemons and hopefully establish a working Internet connectioin).

---

### Post by Extratus on 2011-06-25
Okay thanks, Ill try that.. and let you know how i get on.

---

### Post by Extratus on 2011-06-25
Well it didnt work; it kept attempting to connect, then coming up with Disconnected..

ALSO
Is there any way to Search for networks on Ubuntu?

---

### Post by josephmills on 2011-06-25
please open your terminal  and type in  ```
lspci -nn 
``` look for the ethernet one there might be two please copy that down and let us see it thanks could we also see a ```
sudo lshw -C network 
``` it takes a while to load

---

### Post by Extratus on 2011-06-25
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 [8086:294a] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
0f:00.0 SD Host controller [0805]: Ricoh Co Ltd MMC/SD Host Controller [1180:e822] (rev 01)
0f:00.1 System peripheral [0880]: Ricoh Co Ltd Memory Stick Host Controller [1180:e230] (rev 01)
0f:00.3 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd FireWire Host Controller [1180:e832] (rev 01)



*-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 03
       serial: b8:ac:6f:60:6c:9c
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:45 ioport:ce00(size=256) memory:f0204000-f0204fff memory:f0200000-f0203fff memory:f0220000-f023ffff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 70:f1:a1:5d:8f:5f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-8-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg



So confusing. :]

---

