---
title: "I lost my modem !"
date: 2007-10-18
forum: Networking &amp; Wireless
---

### Post by slink on 2007-10-18
I mean I want to ping my modem but I just don't know what to ping. I have no Internet connection and this is my weird ifconfig:

```
ifconfig
eth0      Link encap:Ethernet  HWaddr   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xb400 

eth0:avah Link encap:Ethernet  HWaddr 0  
          inet addr:169.254.9.22  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0xb400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2280 (2.2 KiB)  TX bytes:2280 (2.2 KiB)

```

You see? No valid IP adress. That 169.254.x.x means I don't revieve DHCP offers. 

So, how can I know my default gateway IP ?

How can I ping my DSL (VT6102 [Rhine-II]) modem ?

---

### Post by slink on 2007-10-18
This is my route:

```
route
Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
link-local      *               255.255.0.0     U     0      0        0 eth0
default         *               0.0.0.0         U     1000   0        0 eth0
```

---

