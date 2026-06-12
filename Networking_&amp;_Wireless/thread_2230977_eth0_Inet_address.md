---
title: "eth0 Inet address"
date: 2014-06-22
forum: Networking &amp; Wireless
---

### Post by Robbyx on 2014-06-22
I am assuming Inet and ip are the same thing in this context. 


```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:7d:0a:01:3e  
          inet addr:192.168.15.2  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:7dff:fe0a:13e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:47112 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32634 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:57013392 (57.0 MB)  TX bytes:5299108 (5.2 MB)

```

My router's address is  192.168.1.1 with an ip subnet mask 255.255.255.0, the dvr is also on the network at 192.168.1.5

My dvr (humax) can not find the dnla server on my main machine (ip address 192.168.15.1)  

I am wondering if it is because the first 3 sections of the ip addresses are not matching:

192.168.15.- <>  192.168.1.-

If by changing the ip address of the main machine so that all the attached devices start with 192.168.1,  I wonder if the dnla server will be found by the DVR.

If it does need changing how can I change that  ip address of Eth0 on the main machine?

---

### Post by chili555 on 2014-06-22
> I am wondering if it is because the first 3 sections of the ip addresses are not matching:Exactly correct.> If by changing the ip address of the main machine so that all the attached devices start with 192.168.1, I wonder if the dnla server will be found by the DVR.Probably so.> eth0      Link encap:Ethernet  HWaddr 00:1d:7d:0a:01:3e  
          inet addr:[COLOR="#FF0000"]192.168.15.2[/COLOR]  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:7dff:fe0a:13e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1Where did the highlighted address come from? Is it not attached to the same router?> My router's address is 192.168.1.1 :confused:

---

