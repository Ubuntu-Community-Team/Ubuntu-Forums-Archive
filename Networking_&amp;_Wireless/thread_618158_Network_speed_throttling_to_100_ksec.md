---
title: "Network speed throttling to 100 k/sec"
date: 2007-11-20
forum: Networking &amp; Wireless
---

### Post by thomas.mcmahon on 2007-11-20
Hi Everyone,

Since my upgrade to gutsy I'm having a strange networking problem.

When I first log in after a reboot, my computer downloads fine at my normal speed (around 900 k/sec), I test this by d/ling a file off my isps ftp server with wget.

Then after a while of normal use of the computer the speed throttles down to about 110 k/sec, which I also test in the same way.

When I do a wget of the same file from a different machine on the network, it goes at full speed, so it must be something  on my end.

Anyone have any ideas what could be causing this?

If you need any more info please ask :)

Thanks in advance

---

### Post by thomas.mcmahon on 2007-11-20
Thought my ifconfig output might be helpful.

eth0      Link encap:Ethernet  HWaddr 00:17:31:59:2F:46  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:75 errors:0 dropped:0 overruns:0 frame:0
          TX packets:75 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4054 (3.9 KB)  TX bytes:4054 (3.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:11:50:63:BF:4A  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:50ff:fe63:bf4a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:290892 errors:0 dropped:0 overruns:0 frame:0
          TX packets:167792 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:408987875 (390.0 MB)  TX bytes:17364981 (16.5 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-11-50-63-BF-4A-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

