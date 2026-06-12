---
title: "Wirelss connection fails if router started after Ubuntu"
date: 2008-04-06
forum: Networking &amp; Wireless
---

### Post by gwm on 2008-04-06
Hi,
I believe this is a bug that only relates to wireless connections to an ADSL router.
Apparently this problem is not there with a wired connection to the router.
If I start the router first, all is well. However, Ubuntu doesn't recognize the router if I start it after Ubuntu.
Normally I have everything setup for automatic detection of settings.
I thought to retry it with a fixed IP address. The results were identical. This output is when the IP address was fixed.

**Scenario 1**
First boot PC then switch on Router:-
(Note: no wired connection to router, only radio)

**$ ifconfig**
ath0      Link encap:Ethernet  HWaddr 00:18:E7:1B:AB:E0  
          inet addr:10.0.0.11  Bcast:10.0.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth1      Link encap:Ethernet  HWaddr 00:14:2A:24:A6:47  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xdc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:694 errors:0 dropped:0 overruns:0 frame:0
          TX packets:694 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:42468 (41.4 KB)  TX bytes:42468 (41.4 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-18-E7-1B-AB-E0-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:355 errors:0 dropped:0 overruns:0 frame:120
          TX packets:287 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:27521 (26.8 KB)  TX bytes:15332 (14.9 KB)
          Interrupt:19 

**$ ping 10.0.0.2**
PING 10.0.0.2 (10.0.0.2) 56(84) bytes of data.
From 10.0.0.11 icmp_seq=2 Destination Host Unreachable
From 10.0.0.11 icmp_seq=3 Destination Host Unreachable
From 10.0.0.11 icmp_seq=4 Destination Host Unreachable

--- 10.0.0.2 ping statistics ---
4 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2999ms
, pipe 3


**Scenario 2**
No changes, simply reboot:-

**$ ifconfig**
ath0      Link encap:Ethernet  HWaddr 00:18:E7:1B:AB:E0  
          inet addr:10.0.0.11  Bcast:10.0.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:446 (446.0 b)  TX bytes:6682 (6.5 KB)

eth1      Link encap:Ethernet  HWaddr 00:14:2A:24:A6:47  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0xdc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5656 (5.5 KB)  TX bytes:5656 (5.5 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-18-E7-1B-AB-E0-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1114 errors:0 dropped:0 overruns:0 frame:0
          TX packets:108 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:98150 (95.8 KB)  TX bytes:11058 (10.7 KB)
          Interrupt:19 
[B]
$ ping 10.0.0.2[/B]
PING 10.0.0.2 (10.0.0.2) 56(84) bytes of data.
64 bytes from 10.0.0.2: icmp_seq=1 ttl=128 time=6.69 ms
64 bytes from 10.0.0.2: icmp_seq=2 ttl=128 time=0.771 ms
64 bytes from 10.0.0.2: icmp_seq=3 ttl=128 time=0.769 ms
64 bytes from 10.0.0.2: icmp_seq=4 ttl=128 time=0.751 ms

--- 10.0.0.2 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3002ms
rtt min/avg/max/mdev = 0.751/2.245/6.692/2.567 ms

Perhaps my setup is wrong, but I don't think so. Everything is set for Automatic detection. I do have my PC defined under hosts, with the IP address that it is normally given, so that other shares and things work correctly. I can't think of anything else, so I guess it's a bug.

---

