---
title: "Ubuntu 7.04, Netgear WG11T cards, and WEP"
date: 2007-09-15
forum: Networking &amp; Wireless
---

### Post by nomenklatura on 2007-09-15
Dear all,

I am aware the problem I am reporting is documented in other threads. However after many hours of trying I have still not got anywhere, so I figured a fresh start might be beneficial to myself, and perhaps other beginners also.

I recently upgraded to Ubuntu 7.04 from 6.06, and found that my wireless card, a Netgear WG511T, is no longer able to connect to my wireless router using WEP encryption. What is the solution to this problem?

lspci -vv

```
...
03:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
        Subsystem: Netgear Unknown device 5b00
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 168 (2500ns min, 7000ns max), Cache Line Size: 128 bytes
        Interrupt: pin A routed to IRQ 11
        Region 0: Memory at 2c000000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

```

ifconfig

```
ath0      Link encap:Ethernet  HWaddr 00:0F:B5:AE:49:3B  
          inet6 addr: fe80::20f:b5ff:feae:493b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0      Link encap:Ethernet  HWaddr 00:08:0D:D9:A3:01  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth1      Link encap:Ethernet  HWaddr 00:16:E3:13:AD:3C  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:e3ff:fe13:ad3c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3135 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1905 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2303479 (2.1 MiB)  TX bytes:283331 (276.6 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:300 (300.0 b)  TX bytes:300 (300.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-0F-B5-AE-49-3B-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2576 errors:0 dropped:0 overruns:0 frame:60098
          TX packets:1575 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:247124 (241.3 KiB)  TX bytes:77266 (75.4 KiB)
          Interrupt:11 

```

iwconfig

```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

irda0     no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"BTVOYAGER2091-3D"  Nickname:"BTVOYAGER2091-3D"
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-90 dBm  Noise level=-90 dBm
          Rx invalid nwid:1896  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Again, I apologise if the answer to my problem is elsewhere.

---

### Post by Vadi on 2007-09-17
Well, the wiki says thet card is working great and all, glad I found this post before buying it.

Off to find different card...

---

