---
title: "Internet sharing via crossover cable"
date: 2007-07-29
forum: Networking &amp; Wireless
---

### Post by SnakeHips on 2007-07-29
Hi ,i've read many of the posts with similar problems but I just cant get it to work.

In a nutshell setup is like this

WWW - DSL - UBUNTU (no more xp hurrah!) - crossover cable - xp laptop.

Both machine can *ping* each other but the laptop is unable to resolve any internet address ie: ping google etc and just comes back with "page not found" etc.

here's the output from the ubuntu box ifconfig

pete@myplace:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr ***********************
          inet6 addr: fe80::211:2fff:fe7f:61e1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:421 errors:0 dropped:0 overruns:0 frame:0
          TX packets:385 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:68934 (67.3 KiB)  TX bytes:59470 (58.0 KiB)
          Interrupt:16 

eth0:avah Link encap:Ethernet  HWaddr *******************
          inet addr:169.254.7.214  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:74 errors:0 dropped:0 overruns:0 frame:0
          TX packets:74 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5512 (5.3 KiB)  TX bytes:5512 (5.3 KiB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:84.68.39.87  P-t-P:62.25.198.137  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:5662 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4554 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:7654545 (7.2 MiB)  TX bytes:377267 (368.4 KiB)

Any ideas? ,my hunch is its a *dns* issue but im not sure where to begin....

thanks if you can help.

---

### Post by dmizer on 2007-07-29
add this line:
blacklist ipv6

to the end of /etc/modprobe.d/blacklist

reboot, and try again.

---

### Post by mips on 2007-07-29
> **SnakeHips said:**
> 
Both machine can *ping* each other but the laptop is unable to resolve any internet address ie: ping google etc and just comes back with "page not found" etc.


Can you ping google or any other website by it's IP address ?

---

