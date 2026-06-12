---
title: "ping works, nslookup works but I can only acces few sites with Feisty"
date: 2007-05-19
forum: Networking &amp; Wireless
---

### Post by Scaryman on 2007-05-19
Hello,

I have made a update to Feisty Fawn from Edgy on my Firewall today. But now i hava a problem. I can't access the internet and then not update Strangely ping,ftp,nslookup,gaim and pages like google.com and my own page works. With Edgy i have no Problems with any Sites from a Network PC on the Firewall i can go on every Site.

**cat /etc/resolv.conf**
```
nameserver 213.168.112.60
nameserver 81.173.194.68
```
[B]
ifconfig:[/B]
```
eth0      Link encap:Ethernet  HWaddr 00:16:3E:0C:75:37
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:3eff:fe0c:7537/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:157 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:10389 (10.1 KiB)  TX bytes:636 (636.0 b)

eth1      Link encap:Ethernet  HWaddr 00:50:FC:85:A6:1B
          inet addr:10.0.0.100  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::250:fcff:fe85:a61b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:43 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3778 (3.6 KiB)  TX bytes:3627 (3.5 KiB)
          Interrupt:16 Base address:0x4000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:264 (264.0 b)  TX bytes:264 (264.0 b)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:87.78.255.237  P-t-P:195.14.247.126  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:31 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:2314 (2.2 KiB)  TX bytes:1779 (1.7 KiB)
```
          


**route:**
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.8.0.2        *               255.255.255.255 UH    0      0        0 tun0
cras10k-pg2.net *               255.255.255.255 UH    0      0        0 ppp0
10.0.0.0        *               255.255.255.0   U     0      0        0 eth1
10.8.0.0        10.8.0.2        255.255.255.0   UG    0      0        0 tun0
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
default         *               0.0.0.0         U     0      0        0 ppp0

```

**netstat -r**
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
10.8.0.2        *               255.255.255.255 UH        0 0          0 tun0
cras10k-pg2.net *               255.255.255.255 UH        0 0          0 ppp0
10.0.0.0        *               255.255.255.0   U         0 0          0 eth1
10.8.0.0        10.8.0.2        255.255.255.0   UG        0 0          0 tun0
192.168.0.0     *               255.255.255.0   U         0 0          0 eth0
default         *               0.0.0.0         U         0 0          0 ppp0
```

I have attached my Firewall (Shorewall) conf as tar firle

Sorry for bad spelling. I am German

Thank You for held

Regards
Mark

---

### Post by ctsdownloads on 2007-05-19
Just for giggles, have you tried openDNS?
[http://www.opendns.com/](http://www.opendns.com/)

---

### Post by stewiehnz on 2007-05-19
Try reducing the MTU settings.  I had the same issue following a router upgrade an having this reduced solved the issues.

I did not carry out the change as it was done by our service provider so I don't know where to change the setting however this is what they told me they did.

---

### Post by Scaryman on 2007-05-19
The DNS-Server ist not the Problem i can Ping every side.

At the moment i have a tempory Linux Router (OPEN-WRT) the MTU is the same on Ubuntu

**ifconfig (on the Standalone Router):**
```
br0       Link encap:Ethernet  HWaddr 00:18:F8:38:41:44
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:189304 errors:0 dropped:0 overruns:0 frame:0
          TX packets:311131 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:10359062 (9.8 MiB)  TX bytes:449310543 (428.4 MiB)

eth0      Link encap:Ethernet  HWaddr 00:18:F8:38:41:44
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:510319 errors:0 dropped:0 overruns:0 frame:0
          TX packets:501765 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:469531694 (447.7 MiB)  TX bytes:466842113 (445.2 MiB)
          Interrupt:4

eth1      Link encap:Ethernet  HWaddr 00:18:F8:38:41:46
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:2 Base address:0x5000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING MULTICAST  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:87.78.227.97  P-t-P:195.14.247.126  Mask:255.255.255.255
          UP POINTOPOINT RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:311518 errors:0 dropped:0 overruns:0 frame:0
          TX packets:188545 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:445015599 (424.3 MiB)  TX bytes:9242633 (8.8 MiB)

```

---

### Post by stewiehnz on 2007-05-19
Reduce the MTU on both the eth0 & eth1 interfaces to 1492 from 1500.  Essentially the ports are loosing some critical data from the reply of the websites.

The issues that you are having are exactly the same as I had.  Some pages loaded and others did not.  To make things confusing at the time I could change the proxy server to another office which had a different connection and problem gone (apart from a slow down in  speed).

Have a look at this article from Wikipedia which may explain what is happeing (much better that I can)
[http://en.wikipedia.org/wiki/Maximum_transmission_unit](http://en.wikipedia.org/wiki/Maximum_transmission_unit)

---

### Post by Scaryman on 2007-05-21
Hello,
i have change the MTU to 1400 and 1492 on both interfaces with no result. I can browse on Google and a few Pages that is all.

**ifconfig**
```
eth0      Link encap:Ethernet  HWaddr 00:16:3E:0C:75:37
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:3eff:fe0c:7537/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:623 errors:0 dropped:0 overruns:0 frame:0
          TX packets:90 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:46753 (45.6 KiB)  TX bytes:5782 (5.6 KiB)

eth1      Link encap:Ethernet  HWaddr 00:50:FC:85:A6:1B
          inet addr:10.0.0.100  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::250:fcff:fe85:a61b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:108 errors:0 dropped:0 overruns:0 frame:0
          TX packets:114 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:9396 (9.1 KiB)  TX bytes:15578 (15.2 KiB)
          Interrupt:16 Base address:0x4000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:33 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2745 (2.6 KiB)  TX bytes:2745 (2.6 KiB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:87.79.218.249  P-t-P:195.14.247.126  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:30 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:2374 (2.3 KiB)  TX bytes:9204 (8.9 KiB)
```

---

