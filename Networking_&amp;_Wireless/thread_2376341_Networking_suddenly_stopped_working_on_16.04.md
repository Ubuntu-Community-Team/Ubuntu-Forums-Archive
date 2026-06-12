---
title: "Networking suddenly stopped working on 16.04"
date: 2017-11-01
forum: Networking &amp; Wireless
---

### Post by dean.w.schulze on 2017-11-01
Yesterday morning, October 31, I had to reboot my Dell XPS laptop several times before I could get a network connection of any kind (ethernet or wifi).  This morning I could not get any connection after over a dozen boots.  Clicking on Network in System Settings just hung the dialog.  This laptop has had no problems with networking in the 6 months I've had it until yesterday.  I suspect an automatic upgrade broke something.

Here's what ifconfig -a showed for ethernet:

```
ifconfig -a
enx00e04c0304e8 Link encap:Ethernet  HWaddr 00:e0:4c:03:04:e8  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```


A friend checked it out and found two commands that get my ethernet working (I haven't checked if this works with wifi):

```
sudo ifconfig enx00e04c0304e8 up
sudo dhclient enx00e04c0304e8
```

This got the ethernet started:

```
$ ifconfig -a
enx00e04c0304e8 Link encap:Ethernet  HWaddr 00:e0:4c:03:04:e8  
          inet6 addr: fe80::2e0:4cff:fe03:4e8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4257 (4.2 KB)  TX bytes:2971 (2.9 KB)

```

Does anyone know why this problem would suddenly occur?

Thanks.

---

