---
title: "can't connect from outside network"
date: 2007-06-21
forum: Networking &amp; Wireless
---

### Post by nofrak on 2007-06-21
I'm running Ubuntu server 7.04 with LAMP (and KDE) installed.  The webserver works fine when accessed on my office lan, but times out from an outside network.  The same thing happens when I try to ping or ssh, so it's not an apache problem.  I have a static IP and a hostname that works (again, only on the internal lan).  

Anybody want to take a whack at it?

---

### Post by linuxonbute on 2007-06-21
Please post the output from

ifconfig

---

### Post by nofrak on 2007-06-21
Thanks for replying.

Ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:16:41:EF:40:CB
          inet addr:152.16.133.148  Bcast:152.16.133.191  Mask:255.255.255.192
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:168355 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56873 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:88093342 (84.0 MiB)  TX bytes:8127009 (7.7 MiB)
          Interrupt:16

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8691 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8691 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4227793 (4.0 MiB)  TX bytes:4227793 (4.0 MiB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01
          inet addr:192.168.221.1  Bcast:192.168.221.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1639 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08
          inet addr:192.168.115.1  Bcast:192.168.115.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1638 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
eth0      Link encap:Ethernet  HWaddr 00:16:41:EF:40:CB
          inet addr:152.16.133.148  Bcast:152.16.133.191  Mask:255.255.255.192
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:168355 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56873 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:88093342 (84.0 MiB)  TX bytes:8127009 (7.7 MiB)
          Interrupt:16

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8691 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8691 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4227793 (4.0 MiB)  TX bytes:4227793 (4.0 MiB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01
          inet addr:192.168.221.1  Bcast:192.168.221.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1639 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08
          inet addr:192.168.115.1  Bcast:192.168.115.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1638 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

I turned off IPv6 and added the hostname after 127.0.0.1 in /etc/hosts, and either because of that or because I was more patient, I found that I could indeed connect from the outside, but the initial response is so slow as to seem non-working.

Again, thanks for any help

---

### Post by mips on 2007-06-21
Firestarter !

Or enable IP forwarding and manually do iptables config.

---

### Post by nofrak on 2007-06-22
I'm using kmyfirewall, so the ports are open (which is why it works on the lan).  Here's something new and fun, though - the hostname is alternating resolving between the correct ip and an incorrect ip.  The incorrect one is not any part of my network settings, though it does seem to be on the local network.  This means that exactly half the time I get a timeout.  It literally alternates when I do ping, and I have no idea how to fix it.

Impart your wisdom, oh wise and benevolent community of guru's, 'cause at this point I'm stuck.

---

### Post by kevdog on 2007-06-22
Why do you have two entries for eth0 when you type ifconfig??

What does you /etc/network/interfaces look like?

---

### Post by nofrak on 2007-06-22
> **kevdog said:**
> Why do you have two entries for eth0 when you type ifconfig??

What does you /etc/network/interfaces look like?

Because I'm an idiot, and pasted the output from ifconfig twice without noticing.  Good eye, though.


My /ect/network/interfaces (only once, hopefully):

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# The primary network interface
auto eth0
iface eth0 inet static
address 152.16.133.148
netmask 255.255.255.192
gateway 152.16.133.129


```

Thanks again for any help.

---

