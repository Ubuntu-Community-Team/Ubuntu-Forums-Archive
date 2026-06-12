---
title: "Wireless Ad-hoc network"
date: 2008-09-17
forum: Networking &amp; Wireless
---

### Post by jesperfr on 2008-09-17
Hello,

I'm trying to set up an ad-hoc network between two 8.04 computers.

I've used iwconfig to configure the wireless connection.

If I run iwconfig it now shows:

> wlan0     IEEE 802.11g  ESSID:"test"  Nickname:""
          Mode:Ad-Hoc  Frequency:2.427 GHz  Cell: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


on both computers.

And on my computer with wireless broadband ifconfig reads:

> eth0      Link encap:Ethernet  HWaddr 00:0a:e4:bc:96:47  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16374 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16374 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:819936 (800.7 KB)  TX bytes:819936 (800.7 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.152.58.28  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:7017 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5082 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:8846801 (8.4 MB)  TX bytes:526556 (514.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:18:de:82:4d:8b  
          inet addr:169.254.34.2  Bcast:169.254.255.255  Mask:255.255.0.0
          inet6 addr: fe80::218:deff:fe82:4d8b/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:99 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:17710 (17.2 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-18-DE-82-4D-8B-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



One worked out of the box and the other I have used a windows driver to configure.

Can any on help me with this or point me to where i can find an answer?

Thank you!

---

