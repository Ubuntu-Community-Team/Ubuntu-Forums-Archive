---
title: "[SOLVED] help needed with broadcom bcm4318"
date: 2008-09-01
forum: Networking &amp; Wireless
---

### Post by SAKeeler on 2008-09-01
ok i need some help
i have, as stated, a broadcom bcm4318 linksys card

after installing b43-fwcutter and the firmware i cant connect to the wireless network.  i can select connect to in network manager and it attempts to. but wont connect

ifconfig lists
[PHP]skeeler@MALP:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:00:39:bf:ff:8d  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::200:39ff:febf:ff8d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6188 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7253746 (6.9 MB)  TX bytes:642322 (627.2 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:468 errors:0 dropped:0 overruns:0 frame:0
          TX packets:468 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:23400 (22.8 KB)  TX bytes:23400 (22.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:14:bf:d4:23:c8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-14-BF-D4-23-C8-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/PHP]

i think wmaster0 is preventing the connection from working properly.
i have tried using ndiswrapper as well, to get full connection speed, but that doesnt work either.
how can i remove wmaster0?
much thanx!

---

### Post by SAKeeler on 2008-09-01
issue has been resolved.

i followed the guide posted within this forum one more time and rebooted twice after.  will wonders never cease, it actually worked this time with ndiswrapper.

---

