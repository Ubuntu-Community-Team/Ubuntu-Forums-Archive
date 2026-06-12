---
title: "help with networking please"
date: 2007-07-28
forum: Networking &amp; Wireless
---

### Post by nal on 2007-07-28
my network card keeps confiruging it self to run on netmask 255.255.128 when the rest of everyone is at 255.255.255.0  this is causing me not to be able to configure the rourter from firefox nor see anyone on the network, i can connect to the net though. how do i set it to go back to 255.255.255.0 so i can see everyone else

this is ifconfig

nal@demon:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:E9:B1:43  
          inet addr:192.168.1.160  Bcast:192.168.1.255  Mask:255.255.255.128
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:98 errors:0 dropped:0 overruns:0 frame:0
          TX packets:98 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10705 (10.4 KiB)  TX bytes:10705 (10.4 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:1A:73:1D:DB:AE  
          inet addr:192.168.1.163  Bcast:192.168.1.255  Mask:255.255.255.128
          inet6 addr: fe80::21a:73ff:fe1d:dbae/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1498 errors:0 dropped:1043 overruns:0 frame:0
          TX packets:1716 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:541214 (528.5 KiB)  TX bytes:297000 (290.0 KiB)
          Interrupt:255 Base address:0x8000

---

### Post by noob12 on 2007-07-29
Can you post the output of 

> 
cat /etc/network/interfaces


---

