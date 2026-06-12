---
title: "IPv6"
date: 2010-08-04
forum: New to Ubuntu
---

### Post by Line on 2010-08-04
Hi! I try out IPv6, without any success so far. I have used this tutorial:

[http://www.debiantutorials.net/configuring-ipv6-tunneling-with-aiccu/]("http://www.debiantutorials.net/configuring-ipv6-tunneling-with-aiccu/")

```
anton@anton-laptop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:24:81:23:86:39  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:98400000-98420000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:280 errors:0 dropped:0 overruns:0 frame:0
          TX packets:280 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:22184 (22.1 KB)  TX bytes:22184 (22.1 KB)

sixxs     Link encap:IPv6-in-IPv4  
          inet6 addr: 2001:16d8:ee00:ec::2/64 Scope:Global
          inet6 addr: fe80::c0a8:67/64 Scope:Link
          UP POINTOPOINT RUNNING NOARP  MTU:1280  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:21:6a:0d:30:1e  
          inet addr:192.168.0.103  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::221:6aff:fe0d:301e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1280  Metric:1
          RX packets:5568 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7247 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1506774 (1.5 MB)  TX bytes:5931794 (5.9 MB)

anton@anton-laptop:~$ ping6 ipv6.google.com
PING ipv6.google.com(2a00:1450:8001::93) 56 data bytes
^C
--- ipv6.google.com ping statistics ---
8 packets transmitted, 0 received, 100% packet loss, time 7003ms

anton@anton-laptop:~$ ping6 www.ipv6.sixxs.net
PING www.ipv6.sixxs.net(2001:1af8:1:f006::6) 56 data bytes
^C
--- www.ipv6.sixxs.net ping statistics ---
6 packets transmitted, 0 received, 100% packet loss, time 4999ms

anton@anton-laptop:~$ 

```

Is anyone able to see what is wrong?
Does anyone know a good basic IPv6 tutorial?

---

### Post by ubudog on 2010-08-04
This may help to get started: [https://wiki.ubuntu.com/IPv6]("https://wiki.ubuntu.com/IPv6")  

May help.

---

