---
title: "Dlink 650+ not working (IBM600X)"
date: 2008-06-05
forum: Networking &amp; Wireless
---

### Post by omeron on 2008-06-05
I'm trying to make the @#$%@#% wireless card to work and nothing I do helps (me being new to linux doesn't help either). I'm running the latest Ubuntu version (8.04?)
here are some outputs (having read a zillion posts I figure some outputs might help you):
iwconfig:
lo        no wireless extensions.

irda0     no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"Our_Home_Net"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:8402  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
ifconfig:
ath0      Link encap:Ethernet  HWaddr 00:19:5b:7b:2f:13  
          inet6 addr: fe80::219:5bff:fe7b:2f13/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ath0:avahi Link encap:Ethernet  HWaddr 00:19:5b:7b:2f:13  
          inet addr:169.254.3.92  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth0      Link encap:Ethernet  HWaddr 00:50:8b:59:18:9d  
          inet addr:192.168.1.34  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:8bff:fe59:189d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3619 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3817 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3291990 (3.1 MB)  TX bytes:505773 (493.9 KB)
          Interrupt:3 Base address:0x300 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:280 errors:0 dropped:0 overruns:0 frame:0
          TX packets:280 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14000 (13.6 KB)  TX bytes:14000 (13.6 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-19-5B-7B-2F-13-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15289 errors:0 dropped:0 overruns:0 frame:70143
          TX packets:393 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:1861737 (1.7 MB)  TX bytes:18786 (18.3 KB)
          Interrupt:11 


Thanks a lot for your help.

---

### Post by superprash2003 on 2008-06-05
go to system->administration->network and set ath0 to DHCP mode.. then give a ifconfig output again.. i presume you are already connected to the Our_Home_Net network

---

