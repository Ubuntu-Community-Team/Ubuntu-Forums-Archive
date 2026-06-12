---
title: "Lan keeps disconnecting (?)"
date: 2006-11-01
forum: Networking &amp; Wireless
---

### Post by iraiscoming223 on 2006-11-01
Hello everybody!
I searched this forum and Italian's one as well before posting, but didn't find anything.
From some days on (don't remember about any particular system update) after  about 30mins my internet connection doesn't work anymore.
By "doesn't work" I mean that for Ubuntu I'm still connected to my router, but if I try to reach any url I get no answer.
Trying to understand what was wrong I open my console and...

**Let's try to ping my DNS server (I mean my Dlink DW640T router - or something similar)**:
```
marco@marco-laptop:~$ who
marco    :0           2006-11-01 10:28
marco    pts/0        2006-11-01 10:57 (:0.0)

marco@marco-laptop:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
From 192.168.1.234 icmp_seq=15 Destination Host Unreachable
--- 192.168.1.1 ping statistics ---
20 packets transmitted, 0 received, +1 errors, 100% packet loss, time 83091ms

```

**Let's try to ping Google by IP:**
```
marco@marco-laptop:~$ ping 64.233.167.99
PING 64.233.167.99 (64.233.167.99) 56(84) bytes of data.
From 192.168.1.234 icmp_seq=3 Destination Host Unreachable
From 192.168.1.234 icmp_seq=16 Destination Host Unreachable
--- 64.233.167.99 ping statistics ---
27 packets transmitted, 0 received, +2 errors, 100% packet loss, time 36076ms
```

**Uhm... And what about ifconfig?** (I cleared wireless & i/o connections)
```
marco@marco-laptop:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:00:00:00:00:00 
          inet addr:192.168.1.234  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe00::00f:000f:f080:6700/60 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14171 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15106 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8431232 (8.0 MiB)  TX bytes:7461740 (7.1 MiB)
          Interrupt:169 
```

Let's try to unplug and re-plug my lan cable.
It seems to be connected to the router now, but no DNS resolving (I mean, if I ping an ip everything's ok, but if I try to ping an url it doesn't work anymore):
```
marco@marco-laptop:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=255 time=1.15 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=255 time=0.762 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=255 time=0.771 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=255 time=0.765 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=255 time=0.756 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=255 time=0.785 ms
64 bytes from 192.168.1.1: icmp_seq=7 ttl=255 time=0.786 ms
64 bytes from 192.168.1.1: icmp_seq=8 ttl=255 time=0.774 ms
64 bytes from 192.168.1.1: icmp_seq=9 ttl=255 time=0.760 ms
64 bytes from 192.168.1.1: icmp_seq=10 ttl=255 time=0.775 ms
64 bytes from 192.168.1.1: icmp_seq=11 ttl=255 time=0.753 ms
64 bytes from 192.168.1.1: icmp_seq=12 ttl=255 time=0.792 ms
--- 192.168.1.1 ping statistics ---
12 packets transmitted, 12 received, 0% packet loss, time 11005ms
rtt min/avg/max/mdev = 0.753/0.802/1.152/0.110 ms

marco@marco-laptop:~$ ping 64.233.167.99
PING 64.233.167.99 (64.233.167.99) 56(84) bytes of data.
64 bytes from 64.233.167.99: icmp_seq=1 ttl=243 time=142 ms
64 bytes from 64.233.167.99: icmp_seq=2 ttl=243 time=138 ms
64 bytes from 64.233.167.99: icmp_seq=3 ttl=243 time=138 ms
64 bytes from 64.233.167.99: icmp_seq=4 ttl=243 time=131 ms
64 bytes from 64.233.167.99: icmp_seq=5 ttl=243 time=130 ms
64 bytes from 64.233.167.99: icmp_seq=6 ttl=243 time=163 ms
64 bytes from 64.233.167.99: icmp_seq=7 ttl=243 time=130 ms
--- 64.233.167.99 ping statistics ---
7 packets transmitted, 7 received, 0% packet loss, time 6011ms
rtt min/avg/max/mdev = 130.283/139.394/163.438/10.709 ms

marco@marco-laptop:~$ ping www.google.com
ping: unknown host www.google.com

marco@marco-laptop:~$ ping http://www.google.com
ping: unknown host http://www.google.com

marco@marco-laptop:~$ ping -c 3 google.com
ping: unknown host google.com

```

Let's ask for a new Ip address to the DHCP:
```
marco@marco-laptop:~$ sudo dhclient
Password:
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:00:00:00:00:00
Sending on   LPF/eth1/00:00:00:00:00:00
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12

```

I also tried to set a static IP address, but nothing changed...
What happened to my Edgy?? :(

Thank you all!!
**Note that I removed all MAC addrees from the output...**

P.s.(When I was on Dapper I had the same problem by upgrading the kernel from 2.6.17-10-26 to 2.6.17-10-27 - or something like that ... Now, on Edgy, uname -r shows me: 2.6.17-10-generic)

---

### Post by swamytk on 2006-11-01
What are all the other network based applications/daemons you are running while this error raises? If you are using some network analysis tool with high polling rate, this might have happened.

---

### Post by iraiscoming223 on 2006-11-01
> **swamytk said:**
> What are all the other network based applications/daemons you are running while this error raises? If you are using some network analysis tool with high polling rate, this might have happened.

What do you mean? As far as I know my system I don't use any network analyzer, but the applet in the gnome panel...

How do I know which daemons and/or program concern with network?

nestat -ano   ?

thank u 4 your reply

---

### Post by iraiscoming223 on 2006-11-04
up 	\\:D/

---

### Post by iraiscoming223 on 2006-11-06
Well, I think I discovered something interesting..
I mean: while I was working ubuntu disconnected me unexpectedly so I use the GNOME applet "Network Manager" to gain infos about my netw... It seems all the dns and also the network address are rewritten in such a strange way (in my opinion)...
Does any1 know why this happens??
Thanks in advance!

---

### Post by stream303 on 2006-11-10
Being able to ping but not resolve hostnames in a browser usually indicates some sort of dns problem.  I'd look at your **/etc/resolv.conf** and make sure it has your isp's nameservers listed  first.  If not this might help:

[http://www.ubuntuforums.org/showthread.php?t=282034&highlight=resolv.conf](http://www.ubuntuforums.org/showthread.php?t=282034&highlight=resolv.conf)

I hope this helps if this is the problem..

---

### Post by Iowan on 2006-11-10
DNS that disappears?
[http://www.ubuntuforums.org/showthread.php?t=282034]("http://www.ubuntuforums.org/showthread.php?t=282034")
In brief, the **dhclient** requests stuff you don't particularly want (changed).

---

