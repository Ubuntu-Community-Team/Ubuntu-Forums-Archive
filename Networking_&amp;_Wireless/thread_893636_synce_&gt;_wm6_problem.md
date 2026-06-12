---
title: "synce &gt; wm6 problem"
date: 2008-08-18
forum: Networking &amp; Wireless
---

### Post by ^[H3ad-Tr1p]^ on 2008-08-18
hi friends

I've tried to follow this guide [http://www.synce.org/moin/SynceWithUbuntu](http://www.synce.org/moin/SynceWithUbuntu) to syncing my ipaq hx 4700 but I'd meet a problem

I've followed that how-to till this point:

Connect your device and run 
synce-pls

but it had listed nothing

I've followed some old tread on this forum but I didn't found any solution apparently

I've observed that however my ipaq it's saw by connection becouse if I try to type ifconfig ,after I connect my ipaq by usb I note this:

rndis0    Link encap:Ethernet  HWaddr 80:00:60:0f:e8:00  
          inet addr:169.254.2.2  Bcast:169.254.2.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:7 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:448 (448.0 B)  TX bytes:988 (988.0 B)


and

ping 169.254.2.2
PING 169.254.2.2 (169.254.2.2) 56(84) bytes of data.
64 bytes from 169.254.2.2: icmp_seq=1 ttl=64 time=0.024 ms
64 bytes from 169.254.2.2: icmp_seq=2 ttl=64 time=0.015 ms
64 bytes from 169.254.2.2: icmp_seq=3 ttl=64 time=0.019 ms
64 bytes from 169.254.2.2: icmp_seq=4 ttl=64 time=0.013 ms
64 bytes from 169.254.2.2: icmp_seq=5 ttl=64 time=0.013 ms



so,at this point,someone know how I can proceed?

thanks very mutch for your support

---

