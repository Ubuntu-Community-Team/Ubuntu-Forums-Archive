---
title: "Access openVPN subnet via client on same LAN"
date: 2016-07-05
forum: Networking &amp; Wireless
---

### Post by greatermold on 2016-07-05
Hello,

I've recently successfully configured an openVPN configuration on Ubuntu Server 14.04.4 and very happy with the performance.  

My LAN is configured with a 192.168.1.* paradigm.
My openVPN is configured with a 10.8.0.* paradigm.

The openVPN server is on the same box where I host a Samba Share.  I have a use case where I have a Windows Laptop where software is dependent on a consistent network mapped drive.  When I am on the LAN, I cannot ping the 10.8.0.* address and when I'm on VPN, I cannot ping the 192.168.1.* address.  I'm aware that the router doesn't recognize the VPN network, but I'm on a network with a AT&T router.

What is the easiest way for me to get my laptop to recognize a single IP address no matter if I'm VPN or local?

Thanks"!

---

### Post by Skaperen on 2016-07-05
the box you have OpenVPN running on should have an address in the 192.168.1.0/24 subnet (eth0 or wlan0) and an address in the 10.8.0.0/24 subnet (your tunnel device interface).  access between these subnets depends on enabling forward in the kernel and adding appropriate route.  what parts of the later two things have you done?  can you show the results of these commands done on your gateway box?

> ifconfig -a -v
route -nv
head /proc/sys/net/ipv4/conf/*/forwarding

---

### Post by greatermold on 2016-07-06
Ah, so I haven't done either of those two. I was thinking that I had to modify something within the router to achieve what I'm trying to get at..  So what would be the best/easiest/safest route to go?

1) Allow all devices on the LAN to see the VPN Subnet (10.8.0.0/24) -or - 
2) While on VPN, allow my client to see the LAN Network address ([COLOR=#000000]192.168.1.0/24[/COLOR])

Requested outputs are below.

```

:~$ ifconfig -a -v
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:207856 errors:0 dropped:0 overruns:0 frame:0
          TX packets:207856 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:50861566 (50.8 MB)  TX bytes:50861566 (50.8 MB)


p19p1     Link encap:Ethernet  HWaddr d0:50:99:87:16:76
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:91464527 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38969404 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:120415292749 (120.4 GB)  TX bytes:6427893857 (6.4 GB)
          Interrupt:17


tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:10.8.0.1  P-t-P:10.8.0.1  Mask:255.255.255.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

```

:~$ route -nv
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 p19p1
10.8.0.0        0.0.0.0         255.255.255.0   U     0      0        0 tun0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 p19p1

```

```

:~$ head /proc/sys/net/ipv4/conf/*/forwarding
==> /proc/sys/net/ipv4/conf/all/forwarding <==
1


==> /proc/sys/net/ipv4/conf/default/forwarding <==
1


==> /proc/sys/net/ipv4/conf/lo/forwarding <==
1


==> /proc/sys/net/ipv4/conf/p19p1/forwarding <==
1


==> /proc/sys/net/ipv4/conf/tun0/forwarding <==
1

```

---

### Post by Skaperen on 2016-07-06
you probably want your gateway box to act as a gateway.  route everything it has access to; route whole subnets.  if more than one other box is involved in reaching other subnets, your will need to set different gateway destinations in the various route statements ... for example 3 boxes doing VPNs and one box is a wifi and another is your internet relay.

---

