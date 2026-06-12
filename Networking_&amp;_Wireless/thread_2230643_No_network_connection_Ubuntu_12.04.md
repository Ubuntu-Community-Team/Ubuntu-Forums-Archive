---
title: "No network connection Ubuntu 12.04"
date: 2014-06-20
forum: Networking &amp; Wireless
---

### Post by wmonref on 2014-06-20
Hi! 
I have installed Ubuntu 12.04 on a computer and it has no network/internet acces. It was runnig on Windows before and everything was fine (so there are no cable, NIC, or router problems).
The NIC LEDs are NOT blinking. Also the system shows that wired network is connected with 10MB speed (It should be 100MB). Below are the results of the "troubleshooting" commands 


```


sudo ifconfig -a

eth1      Link encap:Ethernet  HWaddr 00:30:18:68:00:b9  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::230:18ff:fe68:b9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2936 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2936 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:227638 (227.6 KB)  TX bytes:227638 (227.6 KB)

//------------------------------//

lspci

00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P AGP Bridge (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
01:00.0 VGA compatible controller: NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev c1)
02:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

//------------------------------//

sudo ifup eth1

Ignoring unknown interface eth1=eth1.

//------------------------------//

cat /etc/network/interfaces

auto lo
iface lo inet loopback

//------------------------------//

cat /etc/NetworkManager/nm-system-settings.conf

No such file or directory.

//------------------------------//

dmesg | grep -e eth1 -e bcm

[ 3592.016081] 8139too 0000:02:06.0 eth1: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 3604.016092] 8139too 0000:02:06.0 eth1: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 3616.016234] 8139too 0000:02:06.0 eth1: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 3628.016066] 8139too 0000:02:06.0 eth1: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 3640.016082] 8139too 0000:02:06.0 eth1: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 3652.016116] 8139too 0000:02:06.0 eth1: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 3664.016084] 8139too 0000:02:06.0 eth1: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 3676.016074] 8139too 0000:02:06.0 eth1: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 3688.016087] 8139too 0000:02:06.0 eth1: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 3700.016135] 8139too 0000:02:06.0 eth1: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 3712.016091] 8139too 0000:02:06.0 eth1: link up, 100Mbps, full-duplex, lpa 0x45E1
... and many more similar entries (is this normal???)


```

Can someone, please advice me what to do?
Thank you!

---

### Post by TheFu on 2014-06-20
Usually, slower networking means the wrong DNS is being selected. However, it could also be that the wrong driver was selected for the network card - or perhaps the network card isn't well supported.

Things that appear like a broken network often are not. Please run the troubleshooting commands from here:
[http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking)
and report back what worked and what failed so we can really know where the issue lies.  Please copy/paste the exact command AND the exact results.

---

### Post by wmonref on 2014-06-24
Hi!
Thanks for the reply and sorry for my late reply... Here are the outputs of the commands you requested

```

(My router's IP address is 192.168.1.41)

ping 192.168.1.41
PING 192.168.1.41 (192.168.1.41) 56(84) bytes of data.
From 192.168.1.6 icmp_seq=1 Destination Host Unreachable
From 192.168.1.6 icmp_seq=2 Destination Host Unreachable

---
ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
From 192.168.1.6 icmp_seq=1 Destination Host Unreachable
From 192.168.1.6 icmp_seq=2 Destination Host Unreachable

---
ping google.com
ping: unknown host google.com

---
ping localhost
PING localhost (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost (127.0.0.1): icmp_req=1 ttl=64 time=0.062 ms
64 bytes from localhost (127.0.0.1): icmp_req=2 ttl=64 time=0.058 ms

------
dmesg |grep eth[0-9]
[    2.667556] 8139too 0000:02:06.0 eth0: RealTek RTL8139 at 0x0001c000, 00:30:18:68:00:b9, IRQ 17
[    7.983450] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.840910] 8139too 0000:02:06.0 eth1: link up, 100Mbps, full-duplex, lpa 0x45E1
[   31.824055] NETDEV WATCHDOG: eth1 (8139too): transmit queue 0 timed out
[   34.832117] 8139too 0000:02:06.0 eth1: link up, 100Mbps, full-duplex, lpa 0x45E1
[   46.832070] 8139too 0000:02:06.0 eth1: link up, 100Mbps, full-duplex, lpa 0x45E1
[   58.832075] 8139too 0000:02:06.0 eth1: link up, 100Mbps, full-duplex, lpa 0x45E1
[   70.832086] 8139too 0000:02:06.0 eth1: link up, 100Mbps, full-duplex, lpa 0x45E1
[   82.832066] 8139too 0000:02:06.0 eth1: link up, 100Mbps, full-duplex, lpa 0x45E1
[   94.832102] 8139too 0000:02:06.0 eth1: link up, 100Mbps, full-duplex, lpa 0x45E1
[  106.832068] 8139too 0000:02:06.0 eth1: link up, 100Mbps, full-duplex, lpa 0x45E1
[  118.832254] 8139too 0000:02:06.0 eth1: link up, 100Mbps, full-duplex, lpa 0x45E1
[  130.832085] 8139too 0000:02:06.0 eth1: link up, 100Mbps, full-
---------(and many more entries similar to these)

sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:02:06.0
       logical name: eth1
       version: 10
       serial: 00:30:18:68:00:b9
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half ip=192.168.1.6 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:17 ioport:c000(size=256) memory:fb000000-fb0000ff memory:40000000-4000ffff

-------
ifconfig -a
eth1      Link encap:Ethernet  HWaddr 00:30:18:68:00:b9  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::230:18ff:fe68:b9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:683 errors:0 dropped:0 overruns:0 frame:0
          TX packets:683 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:54012 (54.0 KB)  TX bytes:54012 (54.0 KB)

-----
more /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1

-----
route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.1.41    0.0.0.0         UG    0      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth1
192.168.1.0     *               255.255.255.0   U     1      0        0 eth1



```

Thanks.

---

### Post by wmonref on 2014-06-30
Hello, again!

Surprisingly, the network connection started working all by itself :) 
Thanks for your time and information!
 I suppose a moderator can delete this thread.

---

