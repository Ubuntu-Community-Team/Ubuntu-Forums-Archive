---
title: "Router/Firewall/DHCP Problems"
date: 2006-08-10
forum: Networking &amp; Wireless
---

### Post by TheGamingPit on 2006-08-10
Ok, I've been trying to get this set up for a week now. Here's what I've got.

Fiber Connection to the internet using PPPoE Connected to eth0
1GB Switch Connected to eth1
Several Win XP Pro boxes connected to the switch

I can connect to the PPPoE using pppoeconf without a problem
I can install firestarter, but get an "unknown error"
I've also tried webmin, and using dhcp3-server
I've reloaded from scratch thinking I had messed it up many times (15x or more)

The problem is that it is not handing out DHCP addys and even configuring the XP boxes with static IPs doesn't allow to ping to eth1 (192.168.1.1).

Please help, I will do almost anything...

```
pitlord@tgpadmlinux:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:8D:85:EC:3E
          inet6 addr: fe80::250:8dff:fe85:ec3e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4067 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3404 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3261863 (3.1 MiB)  TX bytes:623175 (608.5 KiB)
          Interrupt:217 Base address:0x2000

eth1      Link encap:Ethernet  HWaddr 00:0E:0C:B8:55:B2
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0xac00 Memory:fcfe0000-fd000000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:39 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2708 (2.6 KiB)  TX bytes:2708 (2.6 KiB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:66.172.97.43  P-t-P:66.172.97.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:3909 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3259 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:3166307 (3.0 MiB)  TX bytes:533653 (521.1 KiB)

```

```
#
# Sample configuration file for ISC dhcpd for Debian
#
# $Id: dhcpd.conf,v 1.4.2.2 2002/07/10 03:50:33 peloy Exp $
#

# option definitions common to all supported networks...
option domain-name "fugue.com";
option domain-name-servers 206.130.130.2, 206.130.133.2;

option subnet-mask 255.255.255.224;
default-lease-time 600;
max-lease-time 7200;

subnet 192.168.1.0 netmask 255.255.255.0 {
   range 192.168.1.125 192.168.1.225;
   option broadcast-address 192.168.1.255;
   option routers 192.168.1.1;
}
```


Please let me know if there is anything else you need to help me.
Edit/Delete Message

---

### Post by TheGamingPit on 2006-08-10
[This post]("http://http://ubuntuforums.org/showthread.php?t=91370") fixed it.  The difference seems to be using: 
```
net.ipv4.ip_forward = 1
```
instead of:
```
net/ipv4/ip_forward=1
```

---

