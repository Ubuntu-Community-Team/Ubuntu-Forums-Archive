---
title: "knetworkmanager lists wlan as a wired device"
date: 2006-11-14
forum: Networking &amp; Wireless
---

### Post by shaman11 on 2006-11-14
Hello,

I have the following problem:
Knetworkmanager lists the wlan USB stick as a wired device so I am not able to connect.
The WLAN USB stick is working fine in Windows and did work on Kubuntu dapper before using ndiswrapper and knetworkmanager. After installing Edgy I ran into this problem. Edgy apparently includes the native Ralink driver for the WLAN device however now I got the problem with knetworkmanager.

Here are some more details about my configuration:

Kubuntu Edgy
D-Link G122 Rev. c1

lsusb
Bus 004 Device 003: ID 07d1:3c03 D-Link System
Bus 004 Device 006: ID 0d8c:000c C-Media Electronics, Inc. Audio Adapter
Bus 004 Device 002: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 003: ID 03f0:6204 Hewlett-Packard DeskJet 5150c
Bus 002 Device 002: ID 05d8:4003 Ultima Electronics Corp. Artec E+ 48U
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

Inhalt /etc/network/interfaces
auto lo
iface lo inet loopback

ifconfig
eth0 Protokoll:Ethernet Hardware Adresse 00:0A:E6:62:AE:43
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
Kollisionen:0 SendewarteschlangenlÃ¤nge:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
Interrupt:185 Basisadresse:0xe800

lo Protokoll:Lokale Schleife
inet Adresse:127.0.0.1 Maske:255.0.0.0
inet6 Adresse: ::1/128 GÃ¼ltigkeitsbereich:Maschine
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:64 errors:0 dropped:0 overruns:0 frame:0
TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
Kollisionen:0 SendewarteschlangenlÃ¤nge:0
RX bytes:5184 (5.0 KiB) TX bytes:5184 (5.0 KiB)

wlan0 Protokoll:Ethernet Hardware Adresse 00:15:E9:B9:44:D5
inet6 Adresse: fe80::215:e9ff:feb9:44d5/64 GÃ¼ltigkeitsbereich:Verbindung
UP RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
Kollisionen:0 SendewarteschlangenlÃ¤nge:0
RX bytes:0 (0.0 b) TX bytes:576 (576.0 b)
Basisadresse:0x2000

wmaster0 Protokoll:UNSPEC Hardware Adresse 00-15-E9-B9-44-D5-00-00-00-00-00-00-00-00-00-00
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
Kollisionen:0 SendewarteschlangenlÃ¤nge:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
Basisadresse:0x2000


iwconfig
wmaster0 IEEE 802.11g Frequency:2.412 GHz
RTS thr:off Fragment thr=2346 B

wlan0 IEEE 802.11g ESSID:""
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated
RTS thr:off Fragment thr=2346 B 

Does anybody have an idea what the problem could be?

Thanks

---

