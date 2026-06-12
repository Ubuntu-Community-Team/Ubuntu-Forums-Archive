---
title: "Someone Please Help RTL8187b!"
date: 2008-03-14
forum: Networking &amp; Wireless
---

### Post by Saerone on 2008-03-14
Realtek 8187b on a gateway t-1625 need help. can post any kinda output anyone wants. but right now im kinda helpless. ANY HELP WOULD BE GREAT!!! also, have uninstalled network manager and i'm using Wicd. Thanks

---

### Post by Saerone on 2008-03-14
I'm entirely lost and have  read up on how friendly and helpful the community is PLEASE HELP ME SO I DON'T HAVE TO GO BACK TO BILL!!

---

### Post by treymul on 2008-03-14
I had to install ndiswrapper and use windows drivers to get mine working.  Do a search, there are a few threads dealing with this.

---

### Post by kevdog on 2008-03-14
What kind of laptop do you have?

Can you post
lspci -nn

Your chipset version may be ammenable to the patched realtek driver made by [http://www.datanorth.net/~cuervo/rtl8187b/FAQ.html](http://www.datanorth.net/~cuervo/rtl8187b/FAQ.html)

lspci might not show any wireless cards b/c I know Toshiba did something asinine and made their internal card a usb device.  In that case post

lsusb -vv

---

### Post by rookie2008 on 2008-05-06
Hi,
I just bought a Gateway t-1625 a month ago... and Vista was dragging all my resources down. So I figured why not try something faster. I installed the Ubuntu 8.04 AMD 64 bit desktop edition. I am not having any of the audio problems previously mentioned. However, the ATI drivers seem to be limited due to closed source problems. I am trying to figure out how to install my wifi drivers. I am very new to the whole linux scene; I guess I will try out NDISwrapper.

Here are the stats that I got back from using the commands Temüjin recommended.

sudo update-pciids

--14:26:00-- [http://pciids.sourceforge.net/v2.2/pci.ids.bz2](http://pciids.sourceforge.net/v2.2/pci.ids.bz2)
=> `/usr/share/misc/pci.ids.gz.new'
Resolving pciids.sourceforge.net... 66.35.250.209
Connecting to pciids.sourceforge.net|66.35.250.209|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 132,393 (129K) [text/plain]

100%[====================================>] 132,393 25.82K/s ETA 00:00

14:26:05 (25.79 KB/s) - `/usr/share/misc/pci.ids.gz.new' saved [132393/132393]


sudo lspci

00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
01:05.2 Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)



sudo lshw -C network

*-network
description: Ethernet interface
product: RTL8101E PCI Express Fast Ethernet controller
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:08:00.0
logical name: eth0
version: 01
serial: 00:03:25:59:1e:fa
size: 100MB/s
capacity: 1GB/s
width: 64 bits
clock: 33MHz
capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=66.212.73.14 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s

---

