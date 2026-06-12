---
title: "[SOLVED] (8.04 Server) &amp;quot;connect: Network is unreachable&amp;quot; error after install"
date: 2008-10-21
forum: Networking &amp; Wireless
---

### Post by nexist on 2008-10-21
I just installed Ubuntu Server (so everything is CLI). Oddly, I can access my internal network but not the external. I can connect from my Windows box to my Ubuntu box via SSH, but I cannot ping [www.yahoo.com](www.yahoo.com) from the server:
```
nexist@obelisk:~$ ping www.yahoo.com
connect: Network is unreachable

nexist@obelisk:~$ ping 10.11.93.1
PING 10.11.93.1 (10.11.93.1) 56(84) bytes of data.
64 bytes from 10.11.93.1: icmp_seq=1 ttl=64 time=5.84 ms

nexist@obelisk:~$ ping 208.81.236.21
connect: Network is unreachable
```

I couldn't find anything like this in the forums so I started a new thread. Here are some relevant files & command outputs.
```
nexist@obelisk:~$ sudo lshw -C network
[sudo] password for nexist:
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:06:08.0
       logical name: eth0
       version: 01
       serial: 00:19:d1:62:c4:3a
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A ip=10.11.93.2 latency=32 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
```

```
nexist@obelisk:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
# address 127.0.0.1
# netmask 255.0.0.0

# The primary network interface
auto eth0
iface eth0 inet static
address 10.11.93.2
netmask 255.255.255.0
```

```
nexist@obelisk:~$ cat /etc/resolv.conf
search Ariyas.mine.nu
nameserver 10.11.93.1
nameserver 208.81.236.21
```

I did add a route, the route to my gateway (heimdal) was not originally present. It changed nothing.

```
nexist@obelisk:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         heimdal.Ariyas. 255.255.255.0   UG    0      0        0 eth0
10.11.93.0      *               255.255.255.0   U     0      0        0 eth0
```
Can anyone tell me what is wrong?

---

### Post by Iowan on 2008-10-21
I'll check my setup when I get home, but I wonder if a "gateway" setting in /etc/network /interfaces file would help.

---

### Post by nexist on 2008-10-21
That fixed it. Thank you

---

### Post by Iowan on 2008-10-21
AWWWW... you didn't even give me a chance to check at home. =D>
Glad it worked!

---

