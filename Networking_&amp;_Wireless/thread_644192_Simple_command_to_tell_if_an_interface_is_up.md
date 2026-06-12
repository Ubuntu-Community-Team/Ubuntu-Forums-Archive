---
title: "Simple command to tell if an interface is up"
date: 2007-12-18
forum: Networking &amp; Wireless
---

### Post by HDave on 2007-12-18
Hi -- I am looking for a command or script that will tell me if a particular interface is up.

Something like:

> ifstate -i eth0
> blah  blah blah

I'd like to call it from within conky.

ifconfig tells me the state of all interfaces but it is too verbose.

Thanks!!

---

### Post by jonobr on 2007-12-18
From a terminal 


ifconfig -a

heres the result


eth0      Link encap:Ethernet  HWaddr 10:14:70:AA:69:98  
          inet addr:10.10.10.10  Bcast:10.10.255.255  Mask:255.255.0.0
          inet6 addr: fe80::204:75ff:feaa:6998/64 Scope:Link
         ** UP **BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:936850 errors:0 dropped:0 overruns:1 frame:0
          TX packets:80647 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:155624408 (148.4 MB)  TX bytes:14581575 (13.9 MB)
          Interrupt:16 Base address:0x8c00

---

### Post by HDave on 2007-12-18
Thanks for the quick reply.  I tried that and it said "UP" on every interface...here's what I got back:

```

eth0      Link encap:Ethernet  HWaddr 00:18:8B:BD:2B:4A  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:00:5A:00:08:70  
          inet addr:192.168.253.198  Bcast:192.168.253.255  Mask:255.255.255.0
          inet6 addr: fe80::200:5aff:fe00:870/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1754 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1714 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1650427 (1.5 MB)  TX bytes:235672 (230.1 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:679 (679.0 b)  TX bytes:679 (679.0 b)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:192.168.141.1  Bcast:192.168.141.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:192.168.175.1  Bcast:192.168.175.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:19:7D:8E:93:35  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Memory:ecffc000-ed000000 

```

It even says wlan0 is up and I have my wifi card manually switched off!!!!

---

### Post by A + on 2007-12-18
Two of your interfaces eth1 and vmnet1 have addresses associated (have you two cards?)  Why doesn't the wlan0 interface also have associated inet addr, bcast, mask addresses etc.?  Is it because it's not up?

---

### Post by HDave on 2007-12-18
Good point -- if I grep for the inet addr text I could make it work.

Check this out:

```
ifconfig -s | grep eth0 > /dev/null && ifconfig -a eth0 | grep 'inet addr:' > /dev/null && echo "eth0 is active"

```

---

