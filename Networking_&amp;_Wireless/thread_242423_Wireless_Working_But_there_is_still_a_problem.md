---
title: "Wireless Working But there is still a problem"
date: 2006-08-23
forum: Networking &amp; Wireless
---

### Post by greatmetal on 2006-08-23
I have a USR 5416 and I am using linuxant for the drivers
The problem is it takes forever to connect to sites and and most of the time they will just time out.

Here is my output from iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11-DS  ESSID:"linksys"  Nickname:"unknown"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:66:09:C5:0C
          Bit Rate=54 Mb/s   Tx-Power:0 dBm
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:6/94  Signal level:-70 dBm  Noise level:-154 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:8759   Missed beacon:0


Here is my output if ifconfig -a

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11-DS  ESSID:"linksys"  Nickname:"unknown"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:66:09:C5:0C
          Bit Rate=54 Mb/s   Tx-Power:0 dBm
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:6/94  Signal level:-70 dBm  Noise level:-154 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:8759   Missed beacon:0

greatmetal@greatmetal:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:13:D4:BF:32:80
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217 Base address:0xa800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1184 (1.1 KiB)  TX bytes:1184 (1.1 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:C0:49:D7:AF:FD
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:49ff:fed7:affd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28168 errors:0 dropped:8 overruns:0 frame:0
          TX packets:22584 errors:2 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:30054195 (28.6 MiB)  TX bytes:1727969 (1.6 MiB)

Here is my output of lspci

0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 02)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
0000:00:05.0 IDE interface: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
0000:00:08.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
0000:00:09.0 Communication controller: Conexant HSF 56k Data/Fax Modem
0000:00:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]
0000:01:00.1 Display controller: ATI Technologies Inc RV350 ?? [Radeon 9550] (Secondary)

My kernel is 2.6.15-26-386 Under Ubuntu Linux 6.06

Thank you for your time

---

### Post by meng on 2006-08-23
How far are you from the access point? Link quality of 6/94 is really atrocious!

---

### Post by greatmetal on 2006-08-23
up stairs from the point through brick but windows has no problem

EDIT

Plus my download speeds in linux are 160kb/s but it takes forever to load a webpage

---

### Post by greatmetal on 2006-08-23
:-({|=  :( Bumpedy Bump

---

### Post by greatmetal on 2006-08-23
De Bump masta

---

### Post by greatmetal on 2006-08-24
OMG I FIXED IT i just used swiftfox and everything is fixed

---

