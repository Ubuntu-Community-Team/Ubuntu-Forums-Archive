---
title: "eth1 instead of eth0"
date: 2010-12-04
forum: New to Ubuntu
---

### Post by shankhs on 2010-12-04
Hi,
Whenever I connect to wireless home network and do 
```

ifconfig -a
```

I see my ip address on eth1 and not eth0 like:

```
eth0      Link encap:Ethernet  HWaddr f0:4d:a2:94:2a:8a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:46 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr c0:cb:38:0f:b4:50  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::c2cb:38ff:fe0f:b450/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:146902 errors:0 dropped:0 overruns:0 frame:2885948
          TX packets:118891 errors:13 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:173954162 (173.9 MB)  TX bytes:15829148 (15.8 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:42 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2587 (2.5 KB)  TX bytes:2587 (2.5 KB)
```

How can I connect to eth0 instead of eth1?
I dont have much idea of networking in ubuntu but I am learning.
Thanks for your help.

---

### Post by CharlesA on 2010-12-04
They are two different interfaces.

Your wireless is eth1, wired is eth0.

---

### Post by AlphaLexman on 2010-12-04
> **CharlesA said:**
> They are two different interfaces.

Your wireless is eth1, wired is eth0.

That is not necessarily true... wireless connections are typically wlan0 - wlan1. On the other hand, 'eth1' might be a second wired connection on your network card or motherboard.
> How can I connect to eth0 instead of eth1?
Move the cat5 cable from one port to the other.

To give us more info, post the output of:
```
route
```

---

### Post by CharlesA on 2010-12-04
> **AlphaLexman said:**
> That is not necessarily true... wireless connections are typically wlan0 - wlan1. On the other hand, 'eth1' might be a second wired connection on your network card or motherboard.

True. However, the OP did say that when they were connected to the *wireless network*, eth1 got an IP address. There was also no wlan0 listed in ifconfig.

---

### Post by shankhs on 2010-12-05
> **AlphaLexman said:**
> That is not necessarily true... wireless connections are typically wlan0 - wlan1. On the other hand, 'eth1' might be a second wired connection on your network card or motherboard.

Move the cat5 cable from one port to the other.

To give us more info, post the output of:
```
route
```

I do not have any wired connection.
The output of route:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     2      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth1
```

Can I change my default interface from eth1 to eth0?
I mean is it even possible to switch interfaces? If yes, can you please tell me how.

Thanks

---

### Post by HermanAB on 2010-12-05
Howdy,

Can set the ethernet port name in /etc/udev/rules.d/70-persistent-net.rules.

---

### Post by shankhs on 2010-12-05
Thanks a lot !

---

