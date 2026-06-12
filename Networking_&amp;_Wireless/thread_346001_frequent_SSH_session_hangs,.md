---
title: "frequent SSH session hangs,"
date: 2007-01-25
forum: Networking &amp; Wireless
---

### Post by gnufied on 2007-01-25
Ok, I am asking this question after literally scavenging the internet for every bit of information i can find.

Whenever I connect to remote machines, from my local dapper workstation, my ssh session hangs frequently. I can very well login to remote machines using SSH, work and it would hang abruptly (i.e not a inactivity timeout kinda thing).

I would be editing a small configuration file in Vi and it would hang(i.e no large packet streaming stuff, although I don't know how large is actually a large packet).

Also, when one ssh session to machine X hangs, I would start another session to the same machine, it would work for a while and freeze eventually and oddly enough the other session would become active by then.

My DNS sucks afaik, its kinda slow. but I get this problem, when I ssh to intranet machines also.

Here is the output of ifconfig command from my local machine:

```

eth0      Link encap:Ethernet 
          inet addr:192.168.2.174  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::215:f2ff:fe91:dc77/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:322768 errors:0 dropped:0 overruns:0 frame:0
          TX packets:147062 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:338806200 (323.1 MiB)  TX bytes:10542341 (10.0 MiB)
          Interrupt:217 Base address:0x2000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:62411 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62411 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:14684195 (14.0 MiB)  TX bytes:14684195 (14.0 MiB)

```
Also my machine is:
```
Linux xaos 2.6.15-27-386 #1 PREEMPT Fri Dec 8 17:51:56 UTC 2006 i686 GNU/Linux
```

I am also running firestarter with filter set on machines, where I ssh. Any help is more than welcome.

---

