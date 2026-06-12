---
title: "Internet connection suddenly stopped"
date: 2010-07-03
forum: New to Ubuntu
---

### Post by nageshrk on 2010-07-03
hi, 

I am using ubuntu 10.04, internet connection connection was working fine in ubuntu,
i am having a DSL connection, but suddenly it is not working what can be the problem

---

### Post by Iowan on 2010-07-03
I don't suppose you recently updated? Probably not the answer, but right-click Network Manager and verify Networking is still enabled.

---

### Post by nageshrk on 2010-07-03
i havr verfied with networ connections, when i switch on the modem it shows as 
wired connection 1 connected, but firefox does not open any website.

> **Iowan said:**
> I don't suppose you recently updated? Probably not the answer, but right-click Network Manager and verify Networking is still enabled.

---

### Post by dineshs on 2010-07-04
Pl post the output of
```
ifconfig -a
```
```
route -n
```
and
```
ping -c3 4.2.2.1
```

---

### Post by osix on 2010-10-25
hi,

im also having the same error. my network suddenly stops and will start again after several minutes.

i tried the command given by dineshs. and i got this.

> ubuntu@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:19:d1:fd:6f:bd  
          inet addr:192.168.0.236  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d1ff:fefd:6fbd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:287527 errors:0 dropped:0 overruns:0 frame:0
          TX packets:250794 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:256609217 (256.6 MB)  TX bytes:133413534 (133.4 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:52 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5036 (5.0 KB)  TX bytes:5036 (5.0 KB)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)> ubuntu@ubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.0.139   0.0.0.0         UG    0      0        0 eth0> ubuntu@ubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.0.139   0.0.0.0         UG    0      0        0 eth0then after a while, my networking starts again.

> ubuntu@ubuntu:~$ ping -c3 4.2.2.1
PING 4.2.2.1 (4.2.2.1) 56(84) bytes of data.
64 bytes from 4.2.2.1: icmp_seq=1 ttl=57 time=157 ms
64 bytes from 4.2.2.1: icmp_seq=2 ttl=57 time=160 ms
64 bytes from 4.2.2.1: icmp_seq=3 ttl=57 time=155 msi dont think its my internet connection because my other computer who is connected to the same switch is still connected and my ping continues. i tried to to restart my ubuntu box and i still getting this problem. i notice that after i ran my update manger and install updates, i got this problem.

by the way, im using ubuntu 9.10.

---

