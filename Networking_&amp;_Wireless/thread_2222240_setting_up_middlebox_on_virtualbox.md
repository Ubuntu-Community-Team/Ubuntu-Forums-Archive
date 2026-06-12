---
title: "setting up middlebox on virtualbox"
date: 2014-05-05
forum: Networking &amp; Wireless
---

### Post by sowdust on 2014-05-05
Hi everyone,

I have followed each step of the tutorial as well as all the variants found around the web.

My VM successfully obtains an IP in the expected range but when I try to ping a host, after correctly resolving its ip address, the packets get invariably lost.

My HM route table:
```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 vnet0
172.16.0.0      0.0.0.0         255.255.255.0   U     0      0        0 vnet0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0
```

My HM vnet0 ifconfig:
```
vnet0     Link encap:Ethernet  HWaddr 66:4e:0b:d9:d8:26  
          inet addr:172.16.0.1  Bcast:172.16.0.255  Mask:255.255.255.0
          inet6 addr: fe80::644e:bff:fed9:d826/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:91 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:11165 (11.1 KB)
```

VM route table:
```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         172.16.0.1      0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
172.16.0.0      0.0.0.0         255.255.255.0   U     0      0        0 eth0
```


My networks' knowledge is not enough to imagine where I could be wrong or how to debug... could anyone please help me out with this?
thanks!

---

