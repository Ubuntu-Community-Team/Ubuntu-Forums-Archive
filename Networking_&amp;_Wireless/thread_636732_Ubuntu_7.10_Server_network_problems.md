---
title: "Ubuntu 7.10 Server network problems"
date: 2007-12-10
forum: Networking &amp; Wireless
---

### Post by BBoy on 2007-12-10
Hi!

We have the following HP server at our company with Ubuntu 7.10 Server installed on it:
[**HP ML150G3 WS5130 HP-SATA EU**]("http://h10010.www1.hp.com/wwpc/us/en/sm/WF06a/15351-15351-241434-241646-3328424-1163831.html")

Currently the following services are running on the server:
- Samba server (3.0.26a)
- Squid proxy server (2.6.STABLE14)
- Name server (BIND 9.4.1-P1)
- SMTP daemon (postfix 2.4.5-3ubuntu1)
- Cyrus IMAP daemon (v2.2.13-Debian-2.2.13-11ubuntu1)

lspci output:
```
00:00.0 Host bridge: Intel Corporation 5000V Chipset Memory Controller Hub (rev b1)
00:02.0 PCI bridge: Intel Corporation 5000 Series Chipset PCI Express x8 Port 2-3 (rev b1)
00:03.0 PCI bridge: Intel Corporation 5000 Series Chipset PCI Express x4 Port 3 (rev b1)
00:10.0 Host bridge: Intel Corporation 5000 Series Chipset FSB Registers (rev b1)
00:10.1 Host bridge: Intel Corporation 5000 Series Chipset FSB Registers (rev b1)
00:10.2 Host bridge: Intel Corporation 5000 Series Chipset FSB Registers (rev b1)
00:11.0 Host bridge: Intel Corporation 5000 Series Chipset Reserved Registers (rev b1)
00:13.0 Host bridge: Intel Corporation 5000 Series Chipset Reserved Registers (rev b1)
00:15.0 Host bridge: Intel Corporation 5000 Series Chipset FBD Registers (rev b1)
00:16.0 Host bridge: Intel Corporation 5000 Series Chipset FBD Registers (rev b1)
00:1c.0 PCI bridge: Intel Corporation 631xESB/632xESB/3100 Chipset PCI Express Root Port 1 (rev 09)
00:1d.0 USB Controller: Intel Corporation 631xESB/632xESB/3100 Chipset UHCI USB Controller #1 (rev 09)
00:1d.1 USB Controller: Intel Corporation 631xESB/632xESB/3100 Chipset UHCI USB Controller #2 (rev 09)
00:1d.2 USB Controller: Intel Corporation 631xESB/632xESB/3100 Chipset UHCI USB Controller #3 (rev 09)
00:1d.3 USB Controller: Intel Corporation 631xESB/632xESB/3100 Chipset UHCI USB Controller #4 (rev 09)
00:1d.7 USB Controller: Intel Corporation 631xESB/632xESB/3100 Chipset EHCI USB2 Controller (rev 09)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d9)
00:1f.0 ISA bridge: Intel Corporation 631xESB/632xESB/3100 Chipset LPC Interface Controller (rev 09)
00:1f.1 IDE interface: Intel Corporation 631xESB/632xESB IDE Controller (rev 09)
00:1f.2 RAID bus controller: Intel Corporation 631xESB/632xESB SATA RAID Controller (rev 09)
01:00.0 PCI bridge: Intel Corporation 6311ESB/6321ESB PCI Express Upstream Port (rev 01)
01:00.3 PCI bridge: Intel Corporation 6311ESB/6321ESB PCI Express to PCI-X Bridge (rev 01)
02:00.0 PCI bridge: Intel Corporation 6311ESB/6321ESB PCI Express Downstream Port E1 (rev 01)
04:01.0 Ethernet controller: Intel Corporation 82541PI Gigabit Ethernet Controller (rev 05)
07:01.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5703X Gigabit Ethernet (rev 02)
07:02.0 VGA compatible controller: Matrox Graphics, Inc. MGA G200e [Pilot] ServerEngines (SEP1) (rev 02)
```

First problem was with server that the built-in Gigabit Ethernet controller on the mainboard (regonized as Tigon3 card) cannot run properly at 1 GBps! This problem was resolved by buying a new Intel gigabit LAN card, now it works properly at 1 GBps. 

The main problem is not concerning exactly to above mentioned LAN card problem, but maybe related to it also. We are using about 20-30 pcs of Windows clients with SAMBA server. The server sometimes "playing" that stop responding to requests and lagging about 5-10 seconds with answer. The situations used to came up during simple browsing of the network resources for example. Anyway during this time the server can be reached, *ping *is times are good, just SAMBA makes annoying lags. 

Also I have a little bit different, but maybe related problem also. This is related to proxy server (Squid). Online radio stream doesn´t works good via proxy server, because sometimes it is not starting to play at all on the client or if it´s played the stream has a lot of error during the play. Anyway without proxy online streams are working gorgeously!

Please help me to find out what could be the problem(s) or where to start to find the problem(s)!

Thanks the help in advance!

---

### Post by BBoy on 2008-02-29
Still we have the above mentioned SAMBA related lagging problem. 

I´m looking forward for any helpful answer!

Thanks in advance!

---

