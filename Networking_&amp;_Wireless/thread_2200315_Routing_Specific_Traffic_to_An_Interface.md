---
title: "Routing Specific Traffic to An Interface"
date: 2014-01-18
forum: Networking &amp; Wireless
---

### Post by SlidingHorn on 2014-01-18
I take my own computer to work (long story short, equipment @ work sucks), and have two separate networks there.  One private network (which is very slow, and I don't want to use it unless I have to) I have wired directly into eth0, and the other is wlan0 - a much faster connection that I want to use for most everything.

My employer has several servers to which I would typically connect via SSH.  They have various IPs which are only reachable on the eth0 network at 10.4.0.*

What I want to set up is some sort of rule that automatically sends any traffic destined for one of those servers (i.e. my ssh connections) through eth0, and the rest on wlan0.  I found helgman's response here: [http://ubuntuforums.org/showthread.php?t=1793950&p=10998532#post10998532](http://ubuntuforums.org/showthread.php?t=1793950&p=10998532#post10998532) - but I wanted get some clarification so I know I'm doing it correctly.

Would I essentially have

```
route add default gw WIFIROUTERADDRESS dev wlan0
route add -net 10.4.0.0/24 dev eth0
```

Before making any changes, here's my routing table

```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.99       0.0.0.0         UG    0      0        0 eth0
10.0.0.0        0.0.0.0         255.255.0.0     U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
```

Thanks ahead of time!

*EDIT:  Just to clarify - currently using 12.04, but upgraded the kernel to 3.5.0-45-generic for support for my Ralink 539b*

---

### Post by TheFu on 2014-01-18
That looks right. In the end, you want the "metric" for the wlan0 to be lower (i.e. higher priority) than eth0 metric. I think changing the default route should do that, but if not, then you'll need to do it manually.

---

### Post by SlidingHorn on 2014-01-21
When I attempt to set wlan0 as the gateway, I get the following error:

```
SIOCADDRT: No such process
```

After some Googling, I saw that this usually means that the interface isn't recognized, so I checked out my /etc/network/interfaces:

```
auto lo
iface lo inet loopback

```

I see that there's no mention of eth0 or wlan0...odd, as I know the system sees them

ifconfig -a:
```
ryan@tesla:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr b4:b5:2f:d9:e0:1d  
          inet addr:10.0.0.202  Bcast:10.0.255.255  Mask:255.255.0.0
          inet6 addr: fe80::b6b5:2fff:fed9:e01d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16684 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17989 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7386783 (7.3 MB)  TX bytes:2479656 (2.4 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:988 errors:0 dropped:0 overruns:0 frame:0
          TX packets:988 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:139942 (139.9 KB)  TX bytes:139942 (139.9 KB)

wlan0     Link encap:Ethernet  HWaddr 68:94:23:ae:1f:56  
          inet addr:192.168.2.12  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::6a94:23ff:feae:1f56/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3906 errors:0 dropped:0 overruns:0 frame:0
          TX packets:230 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1175190 (1.1 MB)  TX bytes:28781 (28.7 KB)
```

sudo lshw -C network:
```
ryan@tesla:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: Ralink corp.
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 68:94:23:ae:1f:56
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.5.0-45-generic firmware=0.34 ip=192.168.2.12 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f7c00000-f7c0ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 07
       serial: b4:b5:2f:d9:e0:1d
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=10.0.0.202 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:48 ioport:d000(size=256) memory:f7b04000-f7b04fff memory:f7b00000-f7b03fff

```

All this brings me to my next question:  Should adding the following to my /etc/network/interfaces correct the error I'm getting? 

```
# Set wlan0 as primary interface
iface wlan0 inet dhcp
```

Thanks again for any help you all can provide! :)

---

### Post by TheFu on 2014-01-21
Desktop Ubuntu or Server Ubuntu install?  If desktop, network-manager is the issue/solution.

---

### Post by SlidingHorn on 2014-01-21
> **TheFu said:**
> Desktop Ubuntu or Server Ubuntu install?  If desktop, network-manager is the issue/solution.

Per OP, running Xubuntu 12.04 with updated kernel (3.5.0-45-generic)

EDIT:  It's the desktop version...and what part or function of network-manager is the solution?

---

