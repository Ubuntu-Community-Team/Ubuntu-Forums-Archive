---
title: "Accesing routers results in time out"
date: 2008-04-02
forum: Networking &amp; Wireless
---

### Post by Crash90 on 2008-04-02
I recently set up a Static IP so I could more effeciently used Bit Torrent via port forwarding. This has working with mixed results. 

I was able to access my router until I installed a SNES emulator. For some reason this edited my network interfaces, adding a two extra lines - only allowing me to connect via DHCP.  During this time I was not able to connect to my router it resulted in the connection timing out.

I fixed the problem so that I was able to use my internal static IP address. The problem of not being able to access my router still exists!


Ideas of where to start are greatly apperciated!

---

### Post by superprash2003 on 2008-04-02
please go to the terminal and type ifconfig and post results here.. could be an ip conflict

---

### Post by Crash90 on 2008-04-02
> **superprash2003 said:**
> please go to the terminal and type ifconfig and post results here.. could be an ip conflict


```
 eth0      Link encap:Ethernet  HWaddr 00:12:3F:D9:86:78  
          inet addr:192.168.1.110  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:3fff:fed9:8678/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2855270 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3495047 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1925560728 (1.7 GB)  TX bytes:3065414601 (2.8 GB)
          Interrupt:19 

eth1      Link encap:Ethernet  HWaddr 00:16:6F:1F:1D:C3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:5934393 errors:0 dropped:0 overruns:0 frame:0
          TX packets:322204 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:84 (84.0 b)
          Interrupt:18 Base address:0xc000 Memory:dfcfd000-dfcfdfff 

eth1:avah Link encap:Ethernet  HWaddr 00:16:6F:1F:1D:C3  
          inet addr:169.254.5.149  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:18 Base address:0xc000 Memory:dfcfd000-dfcfdfff 
```

eth0 = wired (which I am using)

eth1 = wireless

---

### Post by superprash2003 on 2008-04-02
are you able to ping your router?

---

### Post by Crash90 on 2008-04-02
> **superprash2003 said:**
> are you able to ping your router?
```
peter@peter-laptop:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

```

I would assume that means no!

---

### Post by Crash90 on 2008-04-03
> **Crash90 said:**
> ```
peter@peter-laptop:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

```

I would assume that means no!



WHOAH! After watching a few hour long tv shows - this shows up in the terminal

```
4 bytes from 192.168.1.1: icmp_seq=5060 ttl=64 time=0.403 ms
64 bytes from 192.168.1.1: icmp_seq=5061 ttl=64 time=0.420 ms
64 bytes from 192.168.1.1: icmp_seq=5062 ttl=64 time=0.421 ms
64 bytes from 192.168.1.1: icmp_seq=5063 ttl=64 time=0.546 ms
64 bytes from 192.168.1.1: icmp_seq=5064 ttl=64 time=0.496 ms
64 bytes from 192.168.1.1: icmp_seq=5065 ttl=64 time=0.442 ms
64 bytes from 192.168.1.1: icmp_seq=5066 ttl=64 time=0.431 ms
64 bytes from 192.168.1.1: icmp_seq=5067 ttl=64 time=0.436 ms
64 bytes from 192.168.1.1: icmp_seq=5068 ttl=64 time=0.412 ms
64 bytes from 192.168.1.1: icmp_seq=5069 ttl=64 time=0.409 ms
64 bytes from 192.168.1.1: icmp_seq=5070 ttl=64 time=0.434 ms
64 bytes from 192.168.1.1: icmp_seq=5071 ttl=64 time=0.397 ms
64 bytes from 192.168.1.1: icmp_seq=5072 ttl=64 time=0.407 ms
64 bytes from 192.168.1.1: icmp_seq=5073 ttl=64 time=0.411 ms
64 bytes from 192.168.1.1: icmp_seq=5074 ttl=64 time=0.409 ms
64 bytes from 192.168.1.1: icmp_seq=5075 ttl=64 time=0.404 ms
64 bytes from 192.168.1.1: icmp_seq=5076 ttl=64 time=0.422 ms

```

This goes for a VERY long time. I have no idea the time between when I sent the command and when it actually pinged!

---

### Post by superprash2003 on 2008-04-03
try accessing the router [http://192.168.1.1](http://192.168.1.1) since you can ping

---

