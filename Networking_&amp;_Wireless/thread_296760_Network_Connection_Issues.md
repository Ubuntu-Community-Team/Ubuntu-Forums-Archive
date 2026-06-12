---
title: "Network Connection Issues"
date: 2006-11-10
forum: Networking &amp; Wireless
---

### Post by twistie on 2006-11-10
Okay. I have a few issues with networking on my brand new install of dapper.

I have edited the aliases file to turn ipv6 off and it is off in firefox, but firefox and the terminal server client are the only two things that are able to communicate outside this computer. Before I turned IPV6 off nothing was connecting al all. GAIM, Synaptic and any other programs refuse to connect!

Now here is all the stuff I think you'll need

**cat /etc/network/interfaces:**
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


**ifconfig -a:**
> eth0      Link encap:Ethernet  HWaddr 00:0C:F1:D2:A6:9D
          inet addr:10.1.1.5  Bcast:10.255.255.255  Mask:255.0.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2826 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2942 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2167456 (2.0 MiB)  TX bytes:403830 (394.3 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:315 errors:0 dropped:0 overruns:0 frame:0
          TX packets:315 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:15772 (15.4 KiB)  TX bytes:15772 (15.4 KiB)



route -v:
> Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        *               255.0.0.0       U     0      0        0 eth0
default         mygateway1.ar7  0.0.0.0         UG    0      0        0 eth0


Can anyone help with my problem?

Thanx in advance.

---

### Post by lloyd_b on 2006-11-10
Could you post your "etc/resolv.conf" file?  

Just to verify, in a terminal window:

```
ping www.yahoo.com
```

Does this reach Yahoo?  If so, then this:

```
ping us.archive.ubuntu.com
```

If this fails, then you've probably got a DNS issue (seeing "resolv.conf" will help sort that out).  If this works, then you probably have a configuration issue in Synaptic.

Lloyd B.

---

