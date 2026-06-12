---
title: "Ubuntu 13.10  RTL8111/8168B problem"
date: 2013-11-27
forum: Networking &amp; Wireless
---

### Post by et_soft on 2013-11-27
After regular update in 13.10 network card was disabled.


```
lshw -C network
```
show that network DISABLED.

after 
```

 sudo ifconfig eth0 down
 sudo ifconfig eth0 up

```
card enabled but receive only ipv6 address and network still nor accessible


```
ifconfig 
eth0      Link encap:Ethernet  HWaddr 8c:89:a5:17:06:c4  
          inet6 addr: fe80::8e89:a5ff:fe17:6c4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:62 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9846 (9.8 KB)  TX bytes:6457 (6.4 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:480 errors:0 dropped:0 overruns:0 frame:0
          TX packets:480 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 

          RX bytes:35264 (35.2 KB)  TX bytes:35264 (35.2 KB)

```

---

