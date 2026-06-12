---
title: "Gutsy - Intel Corporation PRO/Wireless 3945ABG gone"
date: 2007-07-23
forum: Networking &amp; Wireless
---

### Post by andrewsawyer on 2007-07-23
All,

First up - yes, I know Gutsy is going to have these issues, so I'm not complaining.  I would however like to see if I can get a fix.

All was working fine, however I've done a dist-upgrade to the current update and I have 'lost' my wifi.  My outputs are as follows:

```
andrews@andrews-laptop-c210:~$ lspci | grep Wireless
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
andrews@andrews-laptop-c210:~$ ifconfig -a
eth2      Link encap:Ethernet  HWaddr 00:16:36:9A:DF:7A  
          inet addr:192.168.1.107  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fe9a:df7a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14715 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9960 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17871569 (17.0 MB)  TX bytes:1145882 (1.0 MB)
          Interrupt:17 

irda0     Link encap:IrLAP  HWaddr 00:00:00:00  
          NOARP  MTU:2048  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:8 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:500 (500.0 b)  TX bytes:500 (500.0 b)

andrews@andrews-laptop-c210:~$ 
```

The wifi light/button at the front of the laptop (Acer TravelMate C210) is off, but pressing it doesn't do anything.

If anyone could confirm or suggest ways to get the access back, it would be much appreciated.

Cheers,

Andy

---

### Post by madmetal on 2007-07-24
its a known bug..

also reported in launchpad bugs 
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/121439](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/121439)

it would be better to post any further problems to gutsy's testing sub-forum
[http://ubuntuforums.org/forumdisplay.php?f=238](http://ubuntuforums.org/forumdisplay.php?f=238)

---

