---
title: "Networking help"
date: 2006-10-12
forum: Networking &amp; Wireless
---

### Post by Anthony123 on 2006-10-12
Hey I have a problem with my network where ubuntu couldnt find my network drivers any ideas?

---

### Post by jamesr on 2006-10-12
Hi,

Lets start at the begining. Open a terminal window and enter ```
sudo ifconfig -a
```and post the output please.

Also need more information?
desktop or laptop?
wired or wireless?
using a router yes or no?

---

### Post by jackhandy on 2006-10-12
Not trying to steal thread... but here's my info:

sudo ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:50:04:9D:C3:37
          inet addr:192.168.2.26  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::250:4ff:fe9d:c337/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6832 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6396 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:7566602 (7.2 MiB)  TX bytes:937216 (915.2 KiB)
          Interrupt:10 Base address:0x4000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:26 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1848 (1.8 KiB)  TX bytes:1848 (1.8 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

Runnning a P3 500Mhz, 128MB, router

Thanks for anyhelp. Just would like to use the equiv. of network neighborhood, but for xfce. Ubuntu 6.06 installed, w/ xfce.

---

