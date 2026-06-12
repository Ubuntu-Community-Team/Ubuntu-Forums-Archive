---
title: "Internet problem, limited network cabability"
date: 2006-09-07
forum: Networking &amp; Wireless
---

### Post by scratched on 2006-09-07
I'm not sure what happened, but for some reason, I suddenly have limited access to the internet.

The only way I can surf the web is if I use TOR/Privoxy. I can alsopin ping websites (64.233.167.99 for example) (but I can't ping anyone on my LAN).

Other than that, I can't seem to be able to do anything, and even Privoxy seems to be having a hard time (it's slow and doesn't seem to be working as well as it usually does).

The only thing I've done lately to my computer is I install Cisco's VPN client, but the internet was working fine after I stopped using the VPN software today. The vpnclient service is not running though. I made sure of that.

The only cause I can think of was just now when I accidentally put my laptop into suspend mode. When I go into suspend mode, if I try to come out of it, I get this message:
```
[17181278.41600] eth0:NETDEV_TX_BUSY RETURNED;
driver should report queue full via ieee_device->is_queue_full.
``` 
and then I have to do a hard shut-down and turn my computer back on to get it working again. After I did that to get back I could no longer connect to the internet.

Does anyone know what I need to do to fix this?

I have my router IP entered as my DNS and just FYI my wireless card is ETH0 and my wired card is ETH1. I connect through eth1 usually unless I'm at school. This really has me stumped.

If it helps, here is also the output of ifconfig:
$ ifconfig
etOther than that, I can't seem to be able to do anything, and even Privoxy seems to be having a hard time (it's slow and doesn't seem to be working as well as it usually does).

The only thing I've done lately to my computer is I install Cisco's VPN client, but the internet was working fine after I stopped using the VPN software today. The vpnclient service is not running though. I made sure of that.

The only cause I can think of was just now when I accidentally put my laptop into suspend mode. When I go into suspend mode, if I try to come out of it, I get this message:
```
[17181278.41600] eth0:NETDEV_TX_BUSY RETURNED;
driver should report queue full via ieee_device->is_queue_full.
``` 
and then I have to do a hard shut-down and turn my computer back on to get it working again. After I did that to get back I could no longer connect to the internet.

Does anyone know what I need to do to fix this?

I have my router IP entered as my DNS and just FYI my wireless card is ETH0 and my wired card is ETH1. I connect through eth1 usually unless I'm at school. This really has me stumped.

If it helps, here is also the output of ifconfig:
```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:12:F0:88:AC:EC
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::212:f0ff:fe88:acec/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:451 errors:0 dropped:0 overruns:0 frame:0
          TX packets:186 errors:0 dropped:0 overruns:0 carrier:0
          collisionh0      Link encap:Ethernet  HWaddr 00:12:F0:88:AC:EC
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::212:f0ff:fe88:acec/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:451 errors:0 dropped:0 overruns:0 frame:0
          TX packets:186 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:25536852 (24.3 MiB)  TX bytes:3702003 (3.5 MiB)
          Interrupt:10 Base address:0x6000 Memory:e0206000-e0206fff

eth1      Link encap:Ethernet  HWaddr 00:12:3F:7F:FA:F1
          inet addr:192.168.0.152  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::212:3fff:fe7f:faf1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21429 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40045 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:6836318 (6.5 MiB)  TX bytes:2566642 (2.4 MiB)
          Interrupt:10

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:276110 errors:0 dropped:0 overruns:0 frame:0
          TX packets:276110 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:60799842 (57.9 MiB)  TX bytes:60799842 (57.9 MiB)

```

And the output of route:
```
$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth1
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
default         192.168.0.1     0.0.0.0         UG    0      0        0 eth1

```

---

