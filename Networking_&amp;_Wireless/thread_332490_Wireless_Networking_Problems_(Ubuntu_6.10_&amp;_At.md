---
title: "Wireless Networking Problems (Ubuntu 6.10 &amp; Atheros AR5211) Toshiba P25-S507 Laptop"
date: 2007-01-06
forum: Networking &amp; Wireless
---

### Post by wshaddix on 2007-01-06
I've recently installed Ubuntu 6.10 on a Toshiba P25-S507 laptop. Install went fine, loving the OS. I'm having a heck of a time getting my built in wireless network card to connect to my router. I've read many posts here about people having trouble with Ubuntu 6.10 and wireless networking and have tried just about everything I've read with no luck. At one point I was able to get Wireless Assistant to see my SSID but it wouldn't connect via DHCP or static ip.

Here is some general info

**cat /etc/network/interfaces**
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto ath0
iface ath0 inet dhcp

**lspci**
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go5200] (rev a1)
02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:02.0 Ethernet controller: Atheros Communications, Inc. AR5211 802.11ab NIC (rev 01)
02:04.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
02:04.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
02:06.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 03)

** lspci -n**
00:00.0 0600: 8086:2570 (rev 02)
00:01.0 0604: 8086:2571 (rev 02)
00:1d.0 0c03: 8086:24d2 (rev 02)
00:1d.1 0c03: 8086:24d4 (rev 02)
00:1d.2 0c03: 8086:24d7 (rev 02)
00:1d.3 0c03: 8086:24de (rev 02)
00:1d.7 0c03: 8086:24dd (rev 02)
00:1e.0 0604: 8086:244e (rev c2)
00:1f.0 0601: 8086:24d0 (rev 02)
00:1f.1 0101: 8086:24db (rev 02)
00:1f.3 0c05: 8086:24d3 (rev 02)
00:1f.5 0401: 8086:24d5 (rev 02)
00:1f.6 0703: 8086:24d6 (rev 02)
01:00.0 0300: 10de:0324 (rev a1)
02:00.0 0c00: 104c:8026
02:01.0 0200: 10ec:8139 (rev 10)
02:02.0 0200: 168c:0012 (rev 01)
02:04.0 0607: 1179:0617 (rev 32)
02:04.1 0607: 1179:0617 (rev 32)
02:06.0 0880: 1179:0805 (rev 03)

** sudo ifup ath0**
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:90:96:59:d2:9a
Sending on   LPF/ath0/00:90:96:59:d2:9a
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


My wired ethernet connection works fine, just the wireless does not. 

If anyone out there has the patience to help me through this I would greatly appreciate it. I'm willing to go read/learn things on my own, I just need proper direction from someone more experienced than I am.

Wes

---

### Post by tturrisi on 2007-01-06
see [http://www.ubuntuforums.org/showthread.php?t=331625](http://www.ubuntuforums.org/showthread.php?t=331625)

---

