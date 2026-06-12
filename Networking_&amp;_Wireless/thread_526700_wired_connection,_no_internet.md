---
title: "wired connection, no internet"
date: 2007-08-15
forum: Networking &amp; Wireless
---

### Post by razorsharpedge on 2007-08-15
Hi. I just loaded 7.04 (my first linux installation) on a box to make it a dual boot machine with xp. I am able to access internet with xp but not Ubuntu. 
I have the eth0 interface set up for DHCP.
I can reach my router (Netopia R910) through firefox but no outside sites.("Server not found" message)
Can some one help me?
Best regards

---

### Post by noob12 on 2007-08-15
We can try if you can find a way to post the output from these commands
```

ifconfig eth0

cat /etc/network/interfaces

cat /etc/resolv.conf

route -n

grep dhclient /var/log/syslog | tail -50

```

---

### Post by razorsharpedge on 2007-08-15
noob12
Excuse my ignorance but how do I post the output from the commands? I'm using a second computer to reply to posts so that I don't have to reboot in windows every time I want to reply.

---

### Post by zek725 on 2007-08-15
> **razorsharpedge said:**
> noob12
Excuse my ignorance but how do I post the output from the commands? I'm using a second computer to reply to posts so that I don't have to reboot in windows every time I want to reply.

from terminal.

---

### Post by noob12 on 2007-08-15
Yes.  That's a problem.   Do you have a flash drive that you can use to copy text files?  If so use that.

Alternatively, you can set up a static address once you've captured the information and then post.

I can give you pretty broad suggestions without seeing this, but not sure those would help.

---

### Post by razorsharpedge on 2007-08-15
O.K. here's the output as requested. I'm going to bed now, but thanks for the help so far. I look forward to receiving any suggestions you may have.

**ifconfig eth0:**
eth0      Link encap:Ethernet  HWaddr 00:01:01:D4:86:B4  
          inet addr:192.168.1.102  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::201:1ff:fed4:86b4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4360 errors:0 dropped:0 overruns:111 frame:0
          TX packets:3208 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1587160 (1.5 MiB)  TX bytes:557182 (544.1 KiB)
          Interrupt:17 Base address:0x4000
 
**cat /etc/network/interfaces:**
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

iface eth0 inet dhcp







auto eth0



** cat /etc/resolv.conf:**
nameserver 192.168.1.1

**route -n:**

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
209.240.120.1   0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
209.240.120.1   0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0

**grep dhclient /var/log/syslog 1 -50:**

 -- renewal in 14 seconds.
/var/log/syslog:Aug 15 21:50:17 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 21:50:17 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog:Aug 15 21:50:17 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 12 seconds.
/var/log/syslog-Aug 15 21:50:17 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 21:50:29 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 21:50:29 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog-Aug 15 21:50:29 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 21:50:29 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 13 seconds.
/var/log/syslog:Aug 15 21:50:42 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 21:50:42 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog-Aug 15 21:50:42 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 21:50:42 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 12 seconds.
/var/log/syslog:Aug 15 21:50:54 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 21:50:54 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog-Aug 15 21:50:54 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 21:50:54 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 15 seconds.
/var/log/syslog:Aug 15 21:51:09 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 21:51:09 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog-Aug 15 21:51:09 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 21:51:09 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 14 seconds.
/var/log/syslog:Aug 15 21:51:23 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 21:51:23 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog-Aug 15 21:51:23 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 21:51:23 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 15 seconds.
/var/log/syslog:Aug 15 21:51:38 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 21:51:38 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog-Aug 15 21:51:38 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 21:51:38 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 16 seconds.
/var/log/syslog:Aug 15 21:51:54 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 21:51:54 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog-Aug 15 21:51:54 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 21:51:54 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 14 seconds.
/var/log/syslog:Aug 15 21:52:08 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 21:52:08 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog-Aug 15 21:52:08 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 21:52:08 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 14 seconds.
/var/log/syslog:Aug 15 21:52:22 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 21:52:22 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog-Aug 15 21:52:22 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 21:52:22 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 15 seconds.
/var/log/syslog:Aug 15 21:52:37 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 21:52:37 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog:Aug 15 21:52:37 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 12 seconds.
/var/log/syslog-Aug 15 21:52:37 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 21:52:49 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 21:52:49 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog-Aug 15 21:52:49 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 21:52:49 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 14 seconds.
/var/log/syslog:Aug 15 21:53:03 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 21:53:03 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog-Aug 15 21:53:03 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 21:53:03 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 14 seconds.
/var/log/syslog:Aug 15 21:53:17 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 21:53:17 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog-Aug 15 21:53:17 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 21:53:17 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 15 seconds.
/var/log/syslog:Aug 15 21:53:32 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 21:53:32 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog-Aug 15 21:53:32 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 21:53:32 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 13 seconds.
/var/log/syslog:Aug 15 21:53:45 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 21:53:45 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog-Aug 15 21:53:45 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 21:53:45 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 12 seconds.
/var/log/syslog:Aug 15 21:53:57 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 21:53:57 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog-Aug 15 21:53:57 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 21:53:57 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 14 seconds.
/var/log/syslog:Aug 15 21:54:11 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 21:54:11 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog-Aug 15 21:54:11 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 21:54:11 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 15 seconds.
/var/log/syslog:Aug 15 21:54:26 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 21:54:26 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog-Aug 15 21:54:26 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 21:54:26 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 15 seconds.
/var/log/syslog:Aug 15 21:54:41 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 21:54:41 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog-Aug 15 21:54:41 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 21:54:41 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 14 seconds.
/var/log/syslog:Aug 15 21:54:55 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 21:54:55 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog:Aug 15 21:54:55 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 13 seconds.
/var/log/syslog-Aug 15 21:54:55 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 21:55:08 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 21:55:08 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog-Aug 15 21:55:08 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 21:55:08 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 14 seconds.
/var/log/syslog:Aug 15 21:55:22 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 21:55:22 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog-Aug 15 21:55:22 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 21:55:22 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 14 seconds.
/var/log/syslog:Aug 15 21:55:36 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 21:55:36 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog-Aug 15 21:55:36 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 21:55:36 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 16 seconds.
/var/log/syslog:Aug 15 21:55:52 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 21:55:52 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog-Aug 15 21:55:52 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 21:55:52 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 14 seconds.
/var/log/syslog:Aug 15 21:56:06 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 21:56:06 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog-Aug 15 21:56:06 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 21:56:06 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 15 seconds.
/var/log/syslog:Aug 15 21:56:21 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 21:56:21 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog-Aug 15 21:56:21 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 21:56:21 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 16 seconds.
/var/log/syslog:Aug 15 21:56:37 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 21:56:37 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog-Aug 15 21:56:37 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 21:56:37 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 13 seconds.
/var/log/syslog:Aug 15 21:56:50 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 21:56:50 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog-Aug 15 21:56:50 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 21:56:50 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 14 seconds.
/var/log/syslog:Aug 15 21:57:04 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 21:57:04 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog:Aug 15 21:57:04 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 14 seconds.
/var/log/syslog-Aug 15 21:57:04 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 21:57:18 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 21:57:18 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog-Aug 15 21:57:18 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 21:57:18 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 14 seconds.
/var/log/syslog:Aug 15 21:57:32 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 21:57:32 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog-Aug 15 21:57:32 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 21:57:32 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 13 seconds.
/var/log/syslog:Aug 15 21:57:45 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 21:57:45 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog:Aug 15 21:57:45 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 15 seconds.
/var/log/syslog-Aug 15 21:57:45 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 21:58:00 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 21:58:00 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog-Aug 15 21:58:00 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 21:58:00 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 15 seconds.
/var/log/syslog:Aug 15 21:58:15 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 21:58:15 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog-Aug 15 21:58:15 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 21:58:15 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 15 seconds.
/var/log/syslog:Aug 15 21:58:30 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 21:58:30 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog-Aug 15 21:58:30 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 21:58:30 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 14 seconds.
/var/log/syslog:Aug 15 21:58:44 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 21:58:44 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog:Aug 15 21:58:44 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 14 seconds.
/var/log/syslog-Aug 15 21:58:44 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 21:58:58 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 21:58:58 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog:Aug 15 21:58:58 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 13 seconds.
/var/log/syslog-Aug 15 21:58:58 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 21:59:11 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 21:59:11 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog-Aug 15 21:59:11 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 21:59:11 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 13 seconds.
/var/log/syslog:Aug 15 21:59:24 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 21:59:24 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog-Aug 15 21:59:24 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 21:59:24 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 14 seconds.
/var/log/syslog:Aug 15 21:59:38 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 21:59:38 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog-Aug 15 21:59:38 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 21:59:38 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 15 seconds.
/var/log/syslog:Aug 15 21:59:53 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 21:59:53 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog-Aug 15 21:59:53 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 21:59:53 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 14 seconds.
/var/log/syslog:Aug 15 22:00:07 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 22:00:07 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog-Aug 15 22:00:07 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 22:00:07 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 13 seconds.
/var/log/syslog:Aug 15 22:00:20 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 22:00:20 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog-Aug 15 22:00:20 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 22:00:20 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 14 seconds.
/var/log/syslog:Aug 15 22:00:34 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 22:00:34 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog-Aug 15 22:00:34 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 22:00:34 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 14 seconds.
/var/log/syslog:Aug 15 22:00:48 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 22:00:48 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog:Aug 15 22:00:48 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 15 seconds.
/var/log/syslog-Aug 15 22:00:48 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 22:01:03 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 22:01:03 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog-Aug 15 22:01:03 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 22:01:03 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 16 seconds.
/var/log/syslog:Aug 15 22:01:19 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 22:01:19 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog-Aug 15 22:01:19 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 22:01:19 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 15 seconds.
/var/log/syslog:Aug 15 22:01:34 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 22:01:34 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog-Aug 15 22:01:34 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 22:01:34 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 14 seconds.
/var/log/syslog:Aug 15 22:01:48 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 22:01:48 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog:Aug 15 22:01:48 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 13 seconds.
/var/log/syslog-Aug 15 22:01:48 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 22:02:01 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 22:02:01 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog-Aug 15 22:02:01 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 22:02:01 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 15 seconds.
/var/log/syslog:Aug 15 22:02:16 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 22:02:16 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog:Aug 15 22:02:16 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 14 seconds.
/var/log/syslog-Aug 15 22:02:16 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 22:02:30 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 22:02:30 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog:Aug 15 22:02:30 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 12 seconds.
/var/log/syslog-Aug 15 22:02:30 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 22:02:42 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 22:02:42 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog-Aug 15 22:02:42 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 22:02:42 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 13 seconds.
/var/log/syslog:Aug 15 22:02:55 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 22:02:55 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog-Aug 15 22:02:55 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 22:02:55 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 14 seconds.
/var/log/syslog:Aug 15 22:03:09 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 22:03:09 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog-Aug 15 22:03:09 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 22:03:09 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 13 seconds.
/var/log/syslog:Aug 15 22:03:22 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 22:03:22 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog-Aug 15 22:03:22 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 22:03:22 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 14 seconds.
/var/log/syslog:Aug 15 22:03:36 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 22:03:36 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog-Aug 15 22:03:36 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 22:03:36 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 15 seconds.
/var/log/syslog:Aug 15 22:03:51 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 22:03:51 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog-Aug 15 22:03:51 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 22:03:51 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 12 seconds.
/var/log/syslog:Aug 15 22:04:03 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 22:04:03 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog:Aug 15 22:04:03 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 14 seconds.
/var/log/syslog-Aug 15 22:04:03 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 22:04:17 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 22:04:17 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog-Aug 15 22:04:17 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 22:04:17 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 14 seconds.
/var/log/syslog:Aug 15 22:04:31 ubuntu-dualboot dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
/var/log/syslog:Aug 15 22:04:31 ubuntu-dualboot dhclient: DHCPACK from 192.168.1.1
/var/log/syslog-Aug 15 22:04:31 ubuntu-dualboot NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
/var/log/syslog:Aug 15 22:04:31 ubuntu-dualboot dhclient: bound to 192.168.1.102 -- renewal in 12 seconds.
grep: 1: No such file or directory
grep: tail: No such file or directory

---

### Post by noob12 on 2007-08-15
You are missing a default gateway route, and your ppp route may be interfering.  I'd suggest you take down the ppp interface.

Your DHCP service should be providing a default route, probably via your router at 192.168.1.1 but it isn't or it got lost.

You should run these commands manually for now:
```

sudo /sbin/ifdown ppp0
sudo route add -net default gw 192.168.1.1 dev eth0

```

We have not validated that your router is providing a DNS proxy service which is what your /etc/resolv.conf would indicate.  If it really is, then the above will probably get you up and running.

Also your DHCP service is only giving you 15 second DHCP leases.  That's sick.  If this is your router, you should set it to give leases at least an hour or several hours long.

Let me know how this goes and we can try to figure out why the default route isn't getting set right.  May need to understand more about your ppp setup.

---

### Post by razorsharpedge on 2007-08-16
> **noob12 said:**
> You are missing a default gateway route, and your ppp route may be interfering.  I'd suggest you take down the ppp interface.

Your DHCP service should be providing a default route, probably via your router at 192.168.1.1 but it isn't or it got lost.

You should run these commands manually for now:
```

sudo /sbin/ifdown ppp0
sudo route add -net default gw 192.168.1.1 dev eth0

```
 sudo /sbin/ifdown ppp0 resulted with:

/sbin/ifdown: interface ppp0 not configured

I ran sudo route add -net default gw 192.168.1.1 dev eth0 but forgot to copy the output. a second running of the command resulted with:

SIOCADDRT: File exists


> **noob12 said:**
> We have not validated that your router is providing a DNS proxy service which is what your /etc/resolv.conf would indicate.  If it really is, then the above will probably get you up and running.

Also your DHCP service is only giving you 15 second DHCP leases.  That's sick.  If this is your router, you should set it to give leases at least an hour or several hours long.

My router settings shows DHCP lease set at 1 hour. Could ubuntu change this some how?

> **noob12 said:**
> 
Let me know how this goes and we can try to figure out why the default route isn't getting set right.  May need to understand more about your ppp setup.

Still no internet access. How do I let you know about ppp setup?
Thanks for you help so far

---

### Post by noob12 on 2007-08-16
You had earlier posted this
> 
**route -n:**

Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
209.240.120.1 0.0.0.0 255.255.255.255 UH 0 0 0 ppp0
192.168.1.0 0.0.0.0 255.255.255.0 U 0 0 0 eth0
169.254.0.0 0.0.0.0 255.255.0.0 U 1000 0 0 eth0
0.0.0.0 0.0.0.0 0.0.0.0 U 0 0 0 ppp0


What ppp0 is is a ppp interface.  According to your /etc/network/interfaces file, you have a ppp configuration called "dsl-provider" on that box.  Is that something you put there?  Maybe you used to connect that way but no longer do.  In any case, if you intend to connect to the internet via your ethernet, then you don't need that there, and it seems to have created an odd route in the routing table.  I'm suggesting that you not run that.   What you can do is comment out or remove the line "**auto dsl-provider**" from your /etc/network/interfaces file and then reboot.

```

xhost +
sudo gedit /etc/network/interfaces

```
Find the line that says **auto dsl-provider**.  Remove that line or put a **#** sign at the beginning of the line.  Save and exit.  

[COLOR="Red"]Then Reboot.[/COLOR]

Then show me the output of
```

route -n

```
again.  If you do not see a line like this
```

0.0.0.0         192.168.1.1      0.0.0.0         UG    0      0        0 eth0

```
then it means you don't have a default route and you should add it by using this command:
```

sudo route add -net default gw 192.168.1.1 dev eth0

```
If you see it there or once you have added it, try this
```

ping 209.131.36.158

```
This is the address of an arbitrary yahoo host.  We want to see if you can get there.


Also on a related but different topic, as I mentioned earlier, I noticed your machine is only getting 15 second DHCP leases.  This is very short.  This means it needs to go back and renew its IP address lease every 15 seconds.   Usually this value is configured in your LAN router.  Can you check your router configuration and make the DHCP lease time more reasonable, like at least 1/2 hour.  Typically on a personal network it is several hours to a day.

---

### Post by razorsharpedge on 2007-08-17
> > **noob12 said:**
> You had earlier posted this


What ppp0 is is a ppp interface.  According to your /etc/network/interfaces file, you have a ppp configuration called "dsl-provider" on that box.  Is that something you put there?  Maybe you used to connect that way but no longer do.  In any case, if you intend to connect to the internet via your ethernet, then you don't need that there, and it seems to have created an odd route in the routing table.  I'm suggesting that you not run that.   What you can do is comment out or remove the line "**auto dsl-provider**" from your /etc/network/interfaces file and then reboot.

```

xhost +
sudo gedit /etc/network/interfaces

```
Find the line that says **auto dsl-provider**.  Remove that line or put a **#** sign at the beginning of the line.  Save and exit.  

[COLOR="Red"]Then Reboot.[/COLOR]

Then show me the output of
```

route -n

```
again.  If you do not see a line like this
```

0.0.0.0         192.168.1.1      0.0.0.0         UG    0      0        0 eth0

```
then it means you don't have a default route and you should add it by using this command:
```

sudo route add -net default gw 192.168.1.1 dev eth0

```
If you see it there or once you have added it, try this
```

ping 209.131.36.158

```
This is the address of an arbitrary yahoo host.  We want to see if you can get there.

I  added the "#"  to the "auto dsl-provider" line and the following shows on the output of the "route -n" command on reboot

```

0.0.0.0         192.168.1.1      0.0.0.0         UG    0      0        0 eth0

``` 

Ping of 209.131.36.158 results in
```
From 192.168.1.1 icmp_seq=1,2,3... Destination Host Unreachable"

```
[QUOTE]
Also on a related but different topic, as I mentioned earlier, I noticed your machine is only getting 15 second DHCP leases.  This is very short.  This means it needs to go back and renew its IP address lease every 15 seconds.   Usually this value is configured in your LAN router.  Can you check your router configuration and make the DHCP lease time more reasonable, like at least 1/2 hour.  Typically on a personal network it is several hours to a day.

Please note in my last post I mentioned that my router settings show DHCP lease time of one hour. I don't know why I'm only getting 15 second leases.

where do I go from here?

---

### Post by razorsharpedge on 2007-08-17
> > **noob12 said:**
> You had earlier posted this


What ppp0 is is a ppp interface.  According to your /etc/network/interfaces file, you have a ppp configuration called "dsl-provider" on that box.  Is that something you put there?  Maybe you used to connect that way but no longer do.  In any case, if you intend to connect to the internet via your ethernet, then you don't need that there, and it seems to have created an odd route in the routing table.  I'm suggesting that you not run that.   What you can do is comment out or remove the line "**auto dsl-provider**" from your /etc/network/interfaces file and then reboot.

```

xhost +
sudo gedit /etc/network/interfaces

```
Find the line that says **auto dsl-provider**.  Remove that line or put a **#** sign at the beginning of the line.  Save and exit.  

[COLOR="Red"]Then Reboot.[/COLOR]

Then show me the output of
```

route -n

```
again.  If you do not see a line like this
```

0.0.0.0         192.168.1.1      0.0.0.0         UG    0      0        0 eth0

```
then it means you don't have a default route and you should add it by using this command:
```

sudo route add -net default gw 192.168.1.1 dev eth0

```
If you see it there or once you have added it, try this
```

ping 209.131.36.158

```
This is the address of an arbitrary yahoo host.  We want to see if you can get there.

I  added the "#"  to the "auto dsl-provider" line and the following shows on the output of the "route -n" command on reboot

```

0.0.0.0         192.168.1.1      0.0.0.0         UG    0      0        0 eth0

``` 

Ping of 209.131.36.158 results in
```
From 192.168.1.1 icmp_seq=1 Destination Host Unreachable
From 192.168.1.1 icmp_seq=2 Destination Host Unreachable
From 192.168.1.1 icmp_seq=3 Destination Host Unreachable
From 192.168.1.1 icmp_seq=4 Destination Host Unreachable
...etc

```
[QUOTE]
Also on a related but different topic, as I mentioned earlier, I noticed your machine is only getting 15 second DHCP leases.  This is very short.  This means it needs to go back and renew its IP address lease every 15 seconds.   Usually this value is configured in your LAN router.  Can you check your router configuration and make the DHCP lease time more reasonable, like at least 1/2 hour.  Typically on a personal network it is several hours to a day.

Please note in my last post I mentioned that my router settings show DHCP lease time of one hour. I don't know why I'm only getting 15 second leases.

where do I go from here?

---

### Post by noob12 on 2007-08-17
> I added the "#" to the "auto dsl-provider" line and the following shows on the output of the "route -n" command on reboot

0.0.0.0         192.168.1.1      0.0.0.0         UG    0      0        0 eth0


That's good.  It picked it up from DHCP automatically. (I'm assuming 192.168.1.1 is your router.) Now you do have the right gateway configured.  Before you didn't, so there was a problem that was addressed by disabling the ppp interface.  Progress.

This message suggests 
> 
Ping of 209.131.36.158 results in

From 192.168.1.1 icmp_seq=1,2,3... Destination Host Unreachable"


This means that your ping is going to the gateway (192.168.1.1) but your router reports it isn't isn't able to reach that yahoo host, and I suspect none of the net.  You can try some other address like that of one of your external name servers to see if you can get there.

Do you have any other hosts that you can verify can reach the net through this router in its present state?   If so try that.  Otherwise I would try power-cycling the router.

> 
Please note in my last post I mentioned that my router settings show DHCP lease time of one hour. I don't know why I'm only getting 15 second leases.


This also might get fixed by power-cycling the router.  I don't know why either.  Maybe it had a previous config when started.

---

### Post by razorsharpedge on 2007-08-18
> **noob12 said:**
> That's good.  It picked it up from DHCP automatically. (I'm assuming 192.168.1.1 is your router.) Now you do have the right gateway configured.  Before you didn't, so there was a problem that was addressed by disabling the ppp interface.  Progress.

This message suggests 


This means that your ping is going to the gateway (192.168.1.1) but your router reports it isn't isn't able to reach that yahoo host, and I suspect none of the net.  You can try some other address like that of one of your external name servers to see if you can get there.

Do you have any other hosts that you can verify can reach the net through this router in its present state?   If so try that.  Otherwise I would try power-cycling the router.



This also might get fixed by power-cycling the router.  I don't know why either.  Maybe it had a previous config when started.

Hi noob12
I am unable to ping any other sites but my routereven after power-cycling router. Internet is accessible through xp on the Ubuntu dual boot machine and through this computer which both run through the same router.
hope you have some other suggestions.
Best regards and thanks.

---

### Post by noob12 on 2007-08-18
Yes.  I'd like to see the output of **ipconfig /all** on your Windows boot up that is connecting properly.
That might help us spot some misconfiguration on your Ubuntu boot.

One more thing.  On your Ubuntu boot, can you show me the output of **sudo iptables -nL** ?
This is on the off chance that you have a firewall rule enabled.

UPDATE:  Please note that I'll be away from the forum for about a week, so I won't be able to respond. That you can ping your router and you have the right default route set suggests that you are pretty close to getting things working.  Some others on the forum may be able to help.

---

