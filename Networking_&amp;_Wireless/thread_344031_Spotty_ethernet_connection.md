---
title: "Spotty ethernet connection"
date: 2007-01-22
forum: Networking &amp; Wireless
---

### Post by herrma29 on 2007-01-22
Hi all, I have had ubuntu up and running on my computer for some time now, but most of that time I was using it at home. I am back at school and am having a lot of trouble with my internet.

In ubuntu, I have a connection when it first starts up. I can connect to the internet and everything, but when I try to download updates for my computer, the internet connection drops and I lose everything. Firefox doesn't work, apt doesn't work; no connection. I have no clue what is going on and I know very little about dealing with internet connections.

I do know that windows works perfectly fine however, and it is frustrating having to use windows rather than ubuntu, but I have to be connected to the internet to get my work done.

If you can help, just let me know the steps I need to follow in order to get my connection up and running and hop back on board with Ubuntu!

---

### Post by herrma29 on 2007-01-23
Bump...I have noticed that my connection only goes down when I try to download updates. 

I don't know if this will help, it is the result of ifconfig -a:

> eth0      Link encap:Ethernet  HWaddr 00:0F:B0:89:11:4E  
          inet addr:35.10.111.124  Bcast:35.15.255.255  Mask:255.248.0.0
          inet6 addr: fe80::20f:b0ff:fe89:114e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7408 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2422 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2824377 (2.6 MiB)  TX bytes:509489 (497.5 KiB)
          Interrupt:177 

eth1      Link encap:Ethernet  HWaddr 00:12:F0:B8:E3:33  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:60469 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3729 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:50 Base address:0x8000 Memory:b8006000-b8006fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


I would really like to resolve these problems, but I simply don't know how to. I would really appreciate some help on this.

---

### Post by herrma29 on 2007-01-27
Anyone?

---

