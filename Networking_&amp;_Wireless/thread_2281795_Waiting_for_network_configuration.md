---
title: "Waiting for network configuration"
date: 2015-06-09
forum: Networking &amp; Wireless
---

### Post by mimac on 2015-06-09
Hi,

I have strange problem with network configuration on Ubuntu Server 14.04 LTS, which I am running in Hyper-V VM.
I have two network interfaces, which connect to two different NIC in host machine. When booting up Ubuntu, it always hangs on:
```
Waiting for network configuration...
Waiting up to 60 more seconds for network configuration...
```
for some time. Then it finish booting, eth0 is working just fine, but I can't ping anything on eth1 network. However I can see packets from other devices on network through tcpdump. I suspect I have some silly mistake somewhere, can you please help me find it?

Here is /etc/network/interfaces:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.15
        netmask 255.255.255.0
        gateway 192.168.1.1

auto eth1
iface eth1 inet static
  address 10.1.2.204
  netmask 255.0.0.0
  gateway 10.1.2.200


```

ifconfig:
```

eth0      Link encap:Ethernet  HWaddr 00:15:5d:01:3b:0a
          inet addr:192.168.1.15  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:5dff:fe01:3b0a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3917 errors:0 dropped:995 overruns:0 frame:0
          TX packets:496 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:296179 (296.1 KB)  TX bytes:74704 (74.7 KB)

eth1      Link encap:Ethernet  HWaddr 00:15:5d:02:3b:0b
          inet addr:10.1.2.204  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::215:5dff:fe02:3b0b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:327 errors:0 dropped:0 overruns:0 frame:0
          TX packets:84 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:16093 (16.0 KB)  TX bytes:7016 (7.0 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:3994 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3994 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:528543 (528.5 KB)  TX bytes:528543 (528.5 KB)

```

---

### Post by TheFu on 2015-06-09
/etc/init/failsafe.conf controls the timeout length.
The netmask for eth1 doesn't look correct.

For the other stuff, please post the output from **route**.

---

### Post by mimac on 2015-06-10
I already edited failsafe.conf, so it boots faster, but I would like to find out the cause of this problem.

Output of route:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         10.1.2.200      0.0.0.0         UG    0      0        0 eth1
10.0.0.0        *               255.0.0.0       U     0      0        0 eth1
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0

```

---

### Post by TheFu on 2015-06-10
> **mimac said:**
> I already edited failsafe.conf, so it boots faster, but I would like to find out the cause of this problem.

Output of route:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         10.1.2.200      0.0.0.0         UG    0      0        0 eth1
10.0.0.0        *               255.0.0.0       U     0      0        0 eth1
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0

```

The 10.x.x.x subnet netmask seems wrong to me. Did the network guy tell you to use that netmask? Do people really use a /8 inside a company?  I've seen 255.255.240.0 in large organizations, but never anything larger.  For getting this to work, I'd disable eth0 (ifdown eth0) and get the 10.x.x.x working first.  I'd put in a metric for the 192/24 network connection - perhaps 100 ... just so it doesn't get hit accidentally.

---

### Post by mimac on 2015-06-11
I could use subnet 255.255.255.0, as all devices on that network has IP 10.1.2.x, but could that really be an issue?

I found out there are some hardware issues with NIC on host machine, I am going to check that in few days.

---

### Post by TheFu on 2015-06-11
You don't just get to pick any netmask you want. It has to come from the network manager. The wrong answer means routing doesn't work.

---

