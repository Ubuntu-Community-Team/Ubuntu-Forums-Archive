---
title: "[Wireless] Inprocomm 2220 e Gutsy"
date: 2007-11-20
forum: Networking &amp; Wireless
---

### Post by francesco_82 on 2007-11-20
Hi, my wireless card is inprocomm 2220. With ubuntu 7.04 i did not have problem, but with gutsy my wireless connection don't work...
I installed WinXP driver with ndiswrapper and this is the result of ndiswrapper -l
```

neti2220 : driver installed
        device (17FE:2220) present

```
this is the result of iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:0 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
and this is ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:02:3F:0A:BB:9C  
          inet addr:192.168.0.103  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3078 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2733 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3154996 (3.0 MB)  TX bytes:541187 (528.5 KB)
          Interrupt:18 Base address:0x2400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:70 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5800 (5.6 KB)  TX bytes:5800 (5.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0E:9B:4D:99:EF  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 Memory:e8200800-e8201000 

```

Can you help me?


P.S. Sorry for my english, i'm italian.....

---

