---
title: "Setting up PAN via bluetooth"
date: 2013-10-02
forum: Networking &amp; Wireless
---

### Post by 7KYFQJL on 2013-10-02
I have connected my phone to my computer via bluetooth and setup I believe what is known as PAN. 'ifconfig' gives the following for its interface:

> bnep0     Link encap:Ethernet  HWaddr g0:18:83:a6:75:a3  
          inet addr:192.168.66.2  Bcast:192.168.66.15  Mask:255.255.255.240
          inet6 addr: fe80::c218:85ff:fea6:15f3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1400  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:702 (702.0 B)  TX bytes:1459 (1.4 KB)

I tried testing internet connectivity using the following:

```
wget --bind-address 192.168.66.2 example.com/foobar.txt
```

This failed.

I then ran a port scan on the bluetooth interface IP address (192.168.66.2), and found its looping back to localhost.

Does anyone know why this is happening and how I can get 'it' working (if you know what I mean)?

---

