---
title: "Wired internet connection speed drops down"
date: 2014-04-19
forum: Networking &amp; Wireless
---

### Post by AlexIlin on 2014-04-19
Hello, I am a new user of x/ubuntu or and linux in general. When I boot xubuntu everything works fine, I get the same speed I get on windows (50-55 mbps) but in thirty minutes or so it drops down to 1 mpbs.

So far I've only tried [turning ipv6 off]("http://askubuntu.com/questions/346126/how-to-disable-ipv6-on-ubuntu"), it didn't help.

I don't know how to fix it, please help me.

---

### Post by TheFu on 2014-04-19
Welcome to the forums.

Linux Troubleshooting: [http://blog.jdpfu.com/2013/08/23/common-answers-for-ubuntu-and-linux-issues](http://blog.jdpfu.com/2013/08/23/common-answers-for-ubuntu-and-linux-issues)
* check the log files
* check the network settings

Is this a wifi or wired connection? Wifi is harder, since there are 500 environmental issues to address (approximately).

I've had an issue, but not delayed.  Seems something about network-manager sets up wifi in-line to my wired connection.

---

### Post by AlexIlin on 2014-04-20
[FONT=arial]It's a wired connection

dmesg |grep eth[0-9]:
```
[COLOR=#222222][    3.028772] 8139too 0000:04:00.0 eth0: RealTek RTL8139 at 0x000000000001d000, 00:e0:4c:57:1b:c6, IRQ 17[/COLOR][   16.498916] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.498921] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   18.978826] 8139too 0000:04:00.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[COLOR=#222222][   19.009887] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready[/COLOR]
```

sudo lshw -C network:
[/FONT]```
*-network                      description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 10
       serial: 00:e0:4c:57:1b:c6
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.83 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:17 ioport:d000(size=256) memory:fb310000-fb3100ff memory:fb300000-fb30ffff
  *-network
       description: Ethernet interface
       product: AR8151 v2.0 Gigabit Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: c0
       serial: bc:5f:f4:0b:87:01
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.1-NAPI latency=0 link=no multicast=yes port=twisted pair
       resources: irq:54 memory:fb200000-fb23ffff ioport:c000(size=128)

```
[FONT=arial]
ifconfig -a:
[/FONT]```
eth0      Link encap:Ethernet  HWaddr 00:e0:4c:57:1b:c6            inet addr:192.168.0.83  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:53551 errors:8 dropped:2 overruns:1 frame:0
          TX packets:39741 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:64137704 (64.1 MB)  TX bytes:4847483 (4.8 MB)


eth1      Link encap:Ethernet  HWaddr bc:5f:f4:0b:87:01  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1757 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1757 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:209435 (209.4 KB)  TX bytes:209435 (209.4 KB)

```
[FONT=arial]
more /etc/resolv.conf:
[/FONT]```
nameserver 127.0.1.1search Dlink

```
[FONT=arial]
route:
 [/FONT]```
Kernel IP routing tableDestination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         Dlink-Router.Dl 0.0.0.0         UG    0      0        0 eth0
192.168.0.0     *               255.255.255.0   U     1      0        0 eth0

```[FONT=arial]
[/FONT]

---

### Post by TheFu on 2014-04-20
Lots of good information in that post. Thanks.

Exactly how are you testing the throughput? iperf?  Almost any other way will really be testing the disk subsystem, not the network for GigE connections.  Over GigE here, I see large file transfers top out around 75MB/s until the disk buffer is full, then it drops to disk speeds - around 20MB/s.  We need to be careful to NOT confuse MB/s and Mb/s.  Network bandwidth specifications are ALWAYS Mb/s ... although programmers almost always talk "MB/s" ... which is 8x more.

It appears that both your ethernet ports support GigE, but something is preventing that connection on eth0. Perhaps the router doesn't support it OR the cable isn't CAT5e or CAT6 (or both).  I would swap the cable on the PC port-side into eth1 just to see if that was the issue. Easy test.

The nameserver setting really should be an IP address, not a DNS name too.  Which Ubuntu release are you running and how did you configure the networking?  /etc/resolv.conf is only for servers prior to 12.04.  In later "server" releases, those settings are part of the "interfaces" file - on desktops, I haven't a clue.  DNS issues (usually settings unless you run an internal DNS) often appear to be slow networks for most people.

Anyway - there doesn't seem to be a definitely answer yet. Check out the cable/router port to get GigE speeds and figure out how to make the nameserver (DNS) use an IP address, not a lookup.

---

### Post by AlexIlin on 2014-04-23
> **TheFu said:**
>  I would swap the cable on the PC port-side into eth1 just to see if that was the issue. Easy test.
Whatever the problem was, now it's solved. Thank you.

I've been using my PCI LAN adapter and not the one in motherboard. Though I don't know what was the problem (connection on windows is fine) it's now fixed.

---

