---
title: "how do you set up 2 network cards?"
date: 2008-04-14
forum: Networking &amp; Wireless
---

### Post by Slapyo on 2008-04-14
eth0 - internal network
eth1 - external network

if we put a gateway in eth0 pages aren't served externally.  we remove the gateway and pages can be served externally.  but now the computer can't surf the web/download updates ... things like that.

any ideas?  i know it's kind of vague, but i'm not sure what information you need.  let me know and i can post up whatever is needed.

---

### Post by Iowan on 2008-04-14
**route -n**?

---

### Post by Slapyo on 2008-04-14
route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
10.71.0.0       0.0.0.0         255.255.240.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         10.71.0.1       0.0.0.0         UG    100    0        0 eth1
```

---

### Post by Slapyo on 2008-04-14
here is a little bit more information.

ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr 00:04:23:88:E9:3C  
          inet addr:192.168.1.23  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::204:23ff:fe88:e93c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:103868 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54896 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:23981199 (22.8 MB)  TX bytes:28427487 (27.1 MB)
          Base address:0x7000 Memory:f0200000-f0220000 

eth1      Link encap:Ethernet  HWaddr 00:04:23:88:EA:26  
          inet addr:10.71.0.117  Bcast:10.71.15.255  Mask:255.255.240.0
          inet6 addr: fe80::204:23ff:fe88:ea26/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30262 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2176 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11327211 (10.8 MB)  TX bytes:1046220 (1021.6 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2860 (2.7 KB)  TX bytes:2860 (2.7 KB)
```
cat /etc/network/interfaces
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth0 inet static
address 192.168.1.23
netmask 255.255.255.0

iface eth1 inet static
address 10.71.0.117
netmask 255.255.240.0
gateway 10.71.0.1





auto eth1

auto eth0
```
lshw -C network
```
  *-network               
       description: Ethernet interface
       product: 82540EM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:04:02.0
       logical name: eth0
       version: 02
       serial: 00:04:23:88:e9:3c
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=N/A ip=192.168.1.23 latency=64 mingnt=255 module=e1000 multicast=yes
  *-network
       description: Ethernet interface
       product: 82557/8/9 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:05:03.0
       logical name: eth1
       version: 0d
       serial: 00:04:23:88:ea:26
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI firmware=N/A ip=10.71.0.117 latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes
```

---

### Post by Iowan on 2008-04-14
Does [this thread]("http://ubuntuforums.org/showthread.php?t=752850") help at all?  It sounds similar.

---

### Post by Slapyo on 2008-04-14
i'll take a look at it tomorrow when i have access to the machine.  thanks.

any other ideas are appreciated.

---

### Post by Slapyo on 2008-04-15
Either it didn't work, or I didn't do something properly.  :/

---

