---
title: "Download speeds limited to bytes to 25 kb/s"
date: 2009-05-23
forum: New to Ubuntu
---

### Post by bamend on 2009-05-23
I'm trying Ubuntu again.  I've installed amd64 Jaunty and get agonizing slow download speeds.  It's not the computer because I get 800 kb/s + on Windows.  I dual boot.  Heres the output of my ipconfig:

eth0      Link encap:Ethernet  HWaddr 00:21:97:da:ec:10  
          inet addr:192.168.1.122  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:97ff:feda:ec10/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14170 errors:6437 dropped:0 overruns:0 frame:6411
          TX packets:14467 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20176602 (20.1 MB)  TX bytes:1353300 (1.3 MB)
          Interrupt:252 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by yeats on 2009-05-23
```
RX packets:14170 **errors:6437** dropped:0 overruns:0 frame:6411
```

You may have noticed this, but there are MANY errors in received packets.  You can verify how often this is happening by doing a ping to google.com (or another website of choice).  That may help you chase down where it's happening.

---

### Post by bamend on 2009-05-23
My wireless card works great but the ethernet card is slow.  Could it be a compatability issue since the windows side doesn't see any problems?

---

### Post by Crandom on 2009-05-23
> **bamend said:**
> RX packets:14170 [color=red]errors:6437[/color] dropped:0 overruns:0 frame:6411

You should not be getting this many errors any edvice, especially not through an ethernet cable.

Do you plug in your ethernet cable to a router or port switch? If so, and you know its ip address (commonly 192.168.1.1 or 192.168.1.2) do a ping command and record the number of dropped packets (Press Ctrl + C to stop it):
```
ping 192.168.1.1
```
Then do the same for Google:
```
ping google.com
```

If your number of dropped packets for the router is less than the number of packets dropped for google, there is a problem with your internet connection - you need to speak with your ISP.

If your number of dropped packets for the router is the same as the number of packets dropped for google, it could either be a problem with your router or your internet connection.


Try using another ethernet cable (if you have one). Make sure there's no dust in the connectors and output the result of 
```
lspci | grep Ethernet
``` (if nothing appears just paste the whole of "lspci" in between <code></code> tags, replacing < and > with [ and ].

---

### Post by bamend on 2009-05-23
Here's the results:

bamend@Server:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=2.24 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=2.20 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=2.01 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=2.65 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=64 time=2.19 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=64 time=2.19 ms
64 bytes from 192.168.1.1: icmp_seq=7 ttl=64 time=2.15 ms
64 bytes from 192.168.1.1: icmp_seq=8 ttl=64 time=2.21 ms
64 bytes from 192.168.1.1: icmp_seq=9 ttl=64 time=1.97 ms
64 bytes from 192.168.1.1: icmp_seq=10 ttl=64 time=1.97 ms
64 bytes from 192.168.1.1: icmp_seq=11 ttl=64 time=1.98 ms
64 bytes from 192.168.1.1: icmp_seq=12 ttl=64 time=2.01 ms
64 bytes from 192.168.1.1: icmp_seq=13 ttl=64 time=1.97 ms
64 bytes from 192.168.1.1: icmp_seq=14 ttl=64 time=2.01 ms
64 bytes from 192.168.1.1: icmp_seq=15 ttl=64 time=2.65 ms
64 bytes from 192.168.1.1: icmp_seq=16 ttl=64 time=2.05 ms
64 bytes from 192.168.1.1: icmp_seq=17 ttl=64 time=4.29 ms
64 bytes from 192.168.1.1: icmp_seq=18 ttl=64 time=2.00 ms
64 bytes from 192.168.1.1: icmp_seq=19 ttl=64 time=1.97 ms
64 bytes from 192.168.1.1: icmp_seq=20 ttl=64 time=1.80 ms
64 bytes from 192.168.1.1: icmp_seq=21 ttl=64 time=3.60 ms
64 bytes from 192.168.1.1: icmp_seq=22 ttl=64 time=2.23 ms
64 bytes from 192.168.1.1: icmp_seq=23 ttl=64 time=2.24 ms
64 bytes from 192.168.1.1: icmp_seq=24 ttl=64 time=2.46 ms
64 bytes from 192.168.1.1: icmp_seq=25 ttl=64 time=2.22 ms
64 bytes from 192.168.1.1: icmp_seq=26 ttl=64 time=2.21 ms
64 bytes from 192.168.1.1: icmp_seq=27 ttl=64 time=2.21 ms
64 bytes from 192.168.1.1: icmp_seq=28 ttl=64 time=3.35 ms
64 bytes from 192.168.1.1: icmp_seq=29 ttl=64 time=1.92 ms
64 bytes from 192.168.1.1: icmp_seq=30 ttl=64 time=1.73 ms
64 bytes from 192.168.1.1: icmp_seq=31 ttl=64 time=2.29 ms
64 bytes from 192.168.1.1: icmp_seq=32 ttl=64 time=2.17 ms
64 bytes from 192.168.1.1: icmp_seq=33 ttl=64 time=2.21 ms
64 bytes from 192.168.1.1: icmp_seq=34 ttl=64 time=2.25 ms
64 bytes from 192.168.1.1: icmp_seq=35 ttl=64 time=1.95 ms
64 bytes from 192.168.1.1: icmp_seq=36 ttl=64 time=1.96 ms
^C
--- 192.168.1.1 ping statistics ---
36 packets transmitted, 36 received, 0% packet loss, time 35037ms
rtt min/avg/max/mdev = 1.730/2.268/4.291/0.503 ms
bamend@Server:~$ ping google.com
PING google.com (74.125.67.100) 56(84) bytes of data.
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=1 ttl=50 time=27.8 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=6 ttl=50 time=28.0 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=10 ttl=50 time=29.4 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=11 ttl=50 time=27.4 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=15 ttl=50 time=27.2 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=16 ttl=50 time=27.2 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=20 ttl=50 time=29.1 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=21 ttl=50 time=30.8 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=25 ttl=50 time=30.0 ms
64 bytes from 74.125.67.100: icmp_seq=26 ttl=50 time=29.1 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=27 ttl=50 time=27.1 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=31 ttl=50 time=28.2 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=32 ttl=50 time=28.0 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=36 ttl=50 time=29.1 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=37 ttl=50 time=28.5 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=41 ttl=50 time=26.9 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=42 ttl=50 time=26.6 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=46 ttl=50 time=28.9 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=47 ttl=50 time=28.8 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=51 ttl=50 time=28.6 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=52 ttl=50 time=28.9 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=56 ttl=50 time=28.3 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=57 ttl=50 time=27.9 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=61 ttl=50 time=30.2 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=62 ttl=50 time=28.1 ms
^C
--- google.com ping statistics ---
62 packets transmitted, 25 received, 59% packet loss, time 75281ms
rtt min/avg/max/mdev = 26.663/28.461/30.819/1.037 ms
bamend@Server:~$ lspci | grep Ethernet
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
01:05.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
bamend@Server:~$

---

