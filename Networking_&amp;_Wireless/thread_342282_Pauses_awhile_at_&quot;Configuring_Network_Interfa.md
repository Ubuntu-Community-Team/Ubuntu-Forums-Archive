---
title: "Pauses awhile at &quot;Configuring Network Interfaces&quot; during boot"
date: 2007-01-19
forum: Networking &amp; Wireless
---

### Post by nyxynyx on 2007-01-19
Hello! Im having problem of having to wait at "Configuring Network Interfaces" for very long during boot. How can i make it faster? Thanks!

---

### Post by nyxynyx on 2007-01-22
Sometimes it just hangs there... Anyone pls?

---

### Post by mrfuzzemz on 2007-03-03
I'm having the same issue.  Have you found a way to speed it up?  Thanks.

---

### Post by Mr. C. on 2007-03-03
This could be a couple of things, but we'll start with the basics:

1) Is your PC connected to a LAN?
If no, disable the network adapter and move on.

2) Is the PC obtaining its IP address automatically, or did you assign it statically?
3) If automatically, does it actually obtain an IP address.
3) What is the output of ifconfig -a
4) From what source did it obtain its IP address?
5) Are the two systems connected with a crossover cable instead of with a switch?

Let's start with answers to these.
MrC

---

### Post by mrfuzzemz on 2007-03-03
My notebook most often connects wirelessly and always using DHCP from a router.  I notice that if I boot up with an Ethernet cable connected to my PC it does not wait on "Configuring Network Interfaces."  I have no problem getting an IP.

Here's my ifconfig -a:
```
eth0      Link encap:Ethernet  HWaddr 00:18:F3:A9:FF:D4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0x2000 

eth1      Link encap:Ethernet  HWaddr 00:19:D2:3A:97:53  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d2ff:fe3a:9753/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2180 errors:1 dropped:172 overruns:0 frame:0
          TX packets:1930 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1420288 (1.3 MiB)  TX bytes:413444 (403.7 KiB)
          Interrupt:16 Base address:0x8000 Memory:fe0ff000-fe0fffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:533 (533.0 b)  TX bytes:533 (533.0 b)

```

What do you think is holding it up?  Thanks so much for your reply.

---

### Post by Mr. C. on 2007-03-03
> **mrfuzzemz said:**
> My notebook most often connects wirelessly and always using DHCP from a router.  I notice that if I boot up with an Ethernet cable connected to my PC it does not wait on "Configuring Network Interfaces."  I have no problem getting an IP.

What do you think is holding it up?  Thanks so much for your reply.

I'm not sure what you mean by "most often connects".  Does that mean you have both connected and one or the other is used?  If so, chose one or the other, and not both at the same time.

Wireless networking, esp. with suboptimal conditions, can take some time before the AP & card associate,  and and IP is returned via DHCP.  And sometimes, association does not occur, but a private, local 169. address is returned.

There could be any number of reaons why your wireless connection is having trouble associating and obtaining an IP from DHCP.

You have to start by isolating various causes, and seeing what works and what doesn't.  For example, does it occur if you assign a static IP to the wireless card?

Wireless drivers under linux are not as mature as drivers for, say those for Windows.  I don't have any definitive answers, without more debugging.

MrC

---

### Post by mrfuzzemz on 2007-03-03
> I'm not sure what you mean by "most often connects". Does that mean you have both connected and one or the other is used? If so, chose one or the other, and not both at the same time.

I know that. What I meant was that I usually connect *only* wirelessly. Thanks for your help.  I'm sure I'll figure it out soon.

---

