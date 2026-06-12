---
title: "[SOLVED] problems connecting to livebox with ubuntu studio"
date: 2007-11-30
forum: Networking &amp; Wireless
---

### Post by TimH1980 on 2007-11-30
Hi,

I marked my other topic as solved because I think I maybe get more replies when I define the topic more..

I have problems connecting to the livebox (orange = provider). 

Ndiswrapper seems to recognize the dongle. 

Here's my output:

tim@ubuntu:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

eth1 IEEE 802.11b/g ESSID:"livebox-df5d" Nickname:"zd1211"
Mode:Managed Frequency:2.472 GHz Access Point: Invalid 
Bit Rate=1 Mb/s 
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

Any help would be more than welcome. In the meantime I'll keep on looking. 

Thanks in advance!

By the way, this is the output for ifconfig:

tim@ubuntu:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:04:76C:03:27 
inet addr:192.168.1.12 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::204:76ff:fedc:327/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:18070 errors:0 dropped:0 overruns:0 frame:0
TX packets:13905 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:20289024 (19.3 MB) TX bytes:2155310 (2.0 MB)
Interrupt:16 Base address:0xaf80 

eth1 Link encap:Ethernet HWaddr 00:60:B3:0D:0C:1D 
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:38 dropped:0 overruns:0 frame:38
TX packets:78 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 b) TX bytes:3744 (3.6 KB)

eth1:avah Link encap:Ethernet HWaddr 00:60:B3:0D:0C:1D 
inet addr:169.254.2.175 Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST MULTICAST MTU:1500 Metric:1

lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:1016 errors:0 dropped:0 overruns:0 frame:0
TX packets:1016 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:81571 (79.6 KB) TX bytes:81571 (79.6 KB)

I'm busy with it for 2 nights allready. I like Ubuntu a lot but this is making me crazy! 

Can somebody please help me out here? 

Thanks in advance! Sorry for making a new topic here, but like I said, I think now the problem is more clear.

---

### Post by TimH1980 on 2007-12-01
This topic can be closed. I solved the problem for now with an rt73 driver using another dongle.

---

