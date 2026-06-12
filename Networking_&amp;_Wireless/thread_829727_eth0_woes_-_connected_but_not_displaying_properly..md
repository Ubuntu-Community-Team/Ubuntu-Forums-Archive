---
title: "eth0 woes - connected but not displaying properly.."
date: 2008-06-15
forum: Networking &amp; Wireless
---

### Post by hopelessone on 2008-06-15
Hi,

I had a few probs in Hardy with a single eth0 conn...

1. Internet kept dropping out every 3-4 mins...[Fix: Change from Roaming mode to DCHP]
[https://bugs.launchpad.net/ubuntu/+s...er/+bug/209280](https://bugs.launchpad.net/ubuntu/+s...er/+bug/209280)

2. No upload display of any kind in System monitor or any other app.

redox@redox-pc:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:4d:8a:3b:1e  
          inet addr:[edited]  Bcast:255.255.255.255  Mask:255.255.255.128
          inet6 addr: fe80::2e0:4dff:fe8a:3b1e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2801808 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2885867 errors:201 dropped:0 overruns:4 carrier:53
          collisions:0 txqueuelen:1000 
          [COLOR="Red"]RX bytes:1963972439 (1.8 GB)  TX bytes:0 (0.0 B)[/COLOR]
          Memory:fde80000-fdec0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2542 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2542 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:944830 (922.6 KB)  TX bytes:944830 (922.6 KB)

redox@redox-pc:~$ lspci|grep -i ethernet
03:00.0 Ethernet controller: Attansic Technology Corp. L2 100 Mbit Ethernet Adapter (rev a0)

Hoping someone can help display upload packets...

Thanks in advance..

---

