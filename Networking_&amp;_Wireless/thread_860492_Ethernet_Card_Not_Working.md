---
title: "Ethernet Card Not Working"
date: 2008-07-15
forum: Networking &amp; Wireless
---

### Post by Gibbs on 2008-07-15
I have an old ethernet card (PCI) I installed a long time ago (talking years). I'm trying to hook up my Playstation 2 but it's not working. I'm going to dump some information here and hopefully some nice person will help me out! :)

[quote=lspci]00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS965 [MuTIOL Media IO] (rev 47)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 190 Gigabit Ethernet Adapter
00:05.0 RAID bus controller: Silicon Integrated Systems [SiS] 182 SATA/RAID Controller (rev 01)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:0a.0 Ethernet controller: Belkin Unknown device 700f (rev 20)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600] (rev a2)[/quote]

[quote=lspci -n]00:00.0 0600: 1039:0760 (rev 03)
00:01.0 0604: 1039:0002
00:02.0 0601: 1039:0965 (rev 47)
00:02.5 0101: 1039:5513 (rev 01)
00:02.7 0401: 1039:7012 (rev a0)
00:03.0 0c03: 1039:7001 (rev 0f)
00:03.1 0c03: 1039:7001 (rev 0f)
00:03.2 0c03: 1039:7001 (rev 0f)
00:03.3 0c03: 1039:7002
00:04.0 0200: 1039:0190
00:05.0 0104: 1039:0182 (rev 01)
00:06.0 0604: 1039:000a
00:07.0 0604: 1039:000a
00:0a.0 0200: 1799:700f (rev 20)
00:18.0 0600: 1022:1100
00:18.1 0600: 1022:1101
00:18.2 0600: 1022:1102
00:18.3 0600: 1022:1103
01:00.0 0300: 10de:00f2 (rev a2)[/quote]

[quote=ifconfig]eth0      Link encap:Ethernet  HWaddr 00:11:d8:13:f9:1e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Base address:0xdead 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3036 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3036 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1724670 (1.6 MB)  TX bytes:1724670 (1.6 MB)

wlan0     Link encap:Ethernet  HWaddr 00:17:3f:d3:6a:c5  
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::217:3fff:fed3:6ac5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5408 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3913 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5431923 (5.1 MB)  TX bytes:545811 (533.0 KB)
          Interrupt:20 Memory:f7ffb400-f7ffb425 [/quote]

I'm assuming I have an SIS ethernet card. I'm using a wireless connection and Firestarter gives me a "eht0 device not ready" (for eth1 too).

Any help, ideas or suggestions greatly appreciated! Thanks!

---

