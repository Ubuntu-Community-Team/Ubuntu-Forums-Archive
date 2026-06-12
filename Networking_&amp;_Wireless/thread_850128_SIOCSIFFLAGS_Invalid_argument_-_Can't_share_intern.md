---
title: "SIOCSIFFLAGS: Invalid argument - Can't share internet"
date: 2008-07-05
forum: Networking &amp; Wireless
---

### Post by Victoroth on 2008-07-05
Hi to everyone ,

When I was with Ubuntu 7.10 , everything was good and I could share my internet with my other PC which runs on Windows XP .Now I updated to Ubuntu 8.04 and I have problem with my second lan card . I have 2 networks card on my computer - the first to connect to the internet , the second to share the internet with my other PC (I don't use modem , cross-cabel).The network cards are the same ! REALTEK SEMICONDUCTOR ltd RTL-8139) , but when I type in terminal :
```
ifconfig eth0 up
``` (eth1 is my card which is directly connected to the internet, eth0 for the sharing)
I get :

**SIOCSIFFLAGS: Invalid argument**

Here is what I got when I typed ifconfig in the terminal :


[B]eth1      Link encap:Ethernet  HWaddr 00:80:1e:12:f8:df  
          inet addr:192.168.194.150  Bcast:192.168.194.255  Mask:255.255.255.0
          inet6 addr: fe80::280:1eff:fe12:f8df/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:489525 errors:0 dropped:0 overruns:0 frame:0
          TX packets:129385 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:181602814 (173.1 MB)  TX bytes:65772155 (62.7 MB)
          Interrupt:17 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2357 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2357 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:111223 (108.6 KB)  TX bytes:111223 (108.6 KB)
[/B]


When I type mii-tool :

[B]SIOCGMIIPHY on 'eth0' failed: Invalid argument
eth1: negotiated 100baseTx-FD, link ok
[/B]

Please help !

---

