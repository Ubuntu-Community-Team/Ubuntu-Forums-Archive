---
title: "Atheros 5006EX 802.11 a/b/g wireless"
date: 2008-10-20
forum: Networking &amp; Wireless
---

### Post by tsedrey on 2008-10-20
Hi guys,

I have searching the internet and these forms for a while trying to find the answer to this question, but I have had no success. I have a Thinkpad T61 on 8.10 beta. All of the problems mentioned WERE THERE in 8.04, so its not an update thing. I have 'unchecked' my restricted driver for my wireless card and I can see all the wireless networks, but when I try to connect to them, it stalls for a while and never works...Bummer. I know my card works because I can connect to these networks in Windows. 

A little information about my card I got off the web:This is a WiFi Adapter that is installed in a Mini-PCI Express slot
Features

* Chipset: Atheros AR5006EX (As printed on card AR5BXB6) or AR5212
* Integrated Mac Processor and Radio Chip: Atheros 5423
* IEEE Standards: 802.11a, 802.11b, 802.11g
* PCI ID: 168c:1014


When I run lspci:
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 140M (rev a1)
03:00.0 Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
15:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
15:00.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev ff)
15:00.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
15:00.5 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 11)


ifconfig:
david@david-laptop:/usr/bin$ ifconfig
ath0 Link encap:Ethernet HWaddr 00:1f:e1:c7:44:b2
inet6 addr: fe80::21f:e1ff:fec7:44b2/64 Scope:Link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

eth0 Link encap:Ethernet HWaddr 00:1c:25:ba:c8:f1
inet addr:129.81.89.116 Bcast:129.81.89.127 Mask:255.255.255.192
inet6 addr: fe80::21c:25ff:feba:c8f1/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:6538 errors:0 dropped:0 overruns:0 frame:0
TX packets:5602 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:100
RX bytes:6427794 (6.4 MB) TX bytes:855287 (855.2 KB)
Memory:fe200000-fe220000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:246 errors:0 dropped:0 overruns:0 frame:0
TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:15416 (15.4 KB) TX bytes:15416 (15.4 KB)

wifi0 Link encap:UNSPEC HWaddr 00-1F-E1-C7-44-B2-30-30-00-00-00-00-00-00-00-00
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:110019 errors:0 dropped:0 overruns:0 frame:267456
TX packets:491 errors:15 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:199
RX bytes:12121002 (12.1 MB) TX bytes:22738 (22.7 KB)
Interrupt:17


Any help either in fixing this solution or pointing me in the direction of a fix is greatly appreciated.
Thank you.

---

### Post by tsedrey on 2008-10-21
So it is picking up my card at least....

*-network
description: Ethernet interface
product: 82566MM Gigabit Network Connection
vendor: Intel Corporation
physical id: 19
bus info: pci@0000:00:19.0
logical name: eth0
version: 03
serial: 00:1c:25:ba:c8:f1
size: 100MB/s
capacity: 1GB/s
width: 32 bits
clock: 33MHz
capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 duplex=full firmware=0.3-0 ip=129.81.89.116 latency=0 link=yes module=e1000e multicast=yes port=twisted pair speed=100MB/s
*-network
description: Wireless interface
product: AR5212 802.11abg NIC
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@0000:03:00.0
logical name: wifi0
version: 01
serial: 00:1f:e1:c7:44:b2
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g

---

