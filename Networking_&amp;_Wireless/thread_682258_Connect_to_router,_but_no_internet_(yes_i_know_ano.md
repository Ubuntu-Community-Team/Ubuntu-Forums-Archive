---
title: "Connect to router, but no internet (yes i know another one)"
date: 2008-01-29
forum: Networking &amp; Wireless
---

### Post by corevette on 2008-01-29
```
corevette@corevette-desktop:~$ ifconfig 
ath0      Link encap:Ethernet  HWaddr 00:0F:B5:F8:1C:1E  
          inet addr:172.16.1.39  Bcast:172.16.255.255  Mask:255.255.0.0 
          inet6 addr: fe80::20f:b5ff:fef8:1c1e/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:892 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:329 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:73547 (71.8 KB)  TX bytes:45871 (44.7 KB) 

eth0      Link encap:Ethernet  HWaddr 00:40:CA:87:FE:55  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:16 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:66 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:5320 (5.1 KB)  TX bytes:5320 (5.1 KB) 

wifi0     Link encap:UNSPEC  HWaddr 00-0F-B5-F8-1C-1E-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:26790 errors:0 dropped:0 overruns:0 frame:3532 
          TX packets:883 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:199 
          RX bytes:1984138 (1.8 MB)  TX bytes:77627 (75.8 KB) 
          Interrupt:19 

```
```
corevette@corevette-desktop:~$ route -n 
Kernel IP routing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 ath0 
172.16.0.0      0.0.0.0         255.255.0.0     U     0      0        0 ath0 
0.0.0.0         172.16.0.1      0.0.0.0         UG    0      0        0 ath0 
```
```
corevette@corevette-desktop:~$ cat /etc/network/interfaces 
auto lo 
iface lo inet loopback 
```
i turned on the computer one day and my Netgear WG311t doesn't work

---

