---
title: "Network interfaces Configuring fail at startup"
date: 2008-10-04
forum: Networking &amp; Wireless
---

### Post by shafin on 2008-10-04
At the startup, I get a Configuring Network interfaces [Fail] for /etc/network/interfaces, when I have text enabled during boot. here my /etc/network/interfaces file:
```
auto lo
iface lo inet loopback


iface ppp0 inet ppp
provider ppp0

auto ppp0

iface eth0 inet dhcp

auto eth0
iface eth0 inet dhcp
```

I use a ppp0 connection which I have to manually connect.

Thanks in advance for helping.

---

### Post by Iowan on 2008-10-05
*Looks* kosher - what are results of **ifconfig -a**?

---

### Post by shafin on 2008-10-13
sorry for the late reply.

Here are the results:

```
eth0      Link encap:Ethernet  HWaddr 00:17:31:52:3f:d0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          LOOPBACK  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:xx.xxx.x.xxx  P-t-P:10.0.0.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:1232 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1262 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:1323264 (1.3 MB)  TX bytes:168924 (168.9 KB)

```

---

### Post by shafin on 2008-10-18
/bump

---

