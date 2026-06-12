---
title: "Slow ethernet speeds on fresh install of ubuntu server 14.04"
date: 2015-02-07
forum: Networking &amp; Wireless
---

### Post by Oscar Garza on 2015-02-07
Hi all,

I just set up a server on my apt, but I am finding that any transfers over the network are very slow, capping at 15 megabytes/s. For reference, I can download faster on my wireless network from steam, capping at just under 18 megabytes/s.

First thing I though was the problem was the ZFS volume, however, testing directly on the drives I get 500MB/s without compression. Then I tried transferring files to the SSD and the speed was the same, the download speed is also the same in either case.

SMB, FTP and SFTP all cap at the same speed around 15MB/s. It is driving me nuts, I am using GigE and Cat5e cable which should support speeds faster than what I am seeing, heck even my wireless is faster.

At first I thought it might be the driver for the NIC, so I downloaded the latest version from Intel (my network chip on my motherboard is Intel I210), got the tar file and used # make install, modprobe igb, then added the modprobe igb to rc.local and ethtool confirms it is using igb driver. So I saw no difference at all.

Here is some output I get:
```
oscar@HTPC:~$ uname -mr
3.13.0-45-generic x86_64
```
```
oscar@HTPC:~$ sudo lshw -C network  *-network
       description: Ethernet interface
       product: I210 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: p2p1
       version: 03
       serial: d0:50:99:53:4f:e6
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=igb driverversion=5.0.5-k duplex=full firmware=3.16, 0x800004d6 ip=192.168.1.252 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:18 memory:f7200000-f727ffff ioport:d000(size=32) memory:f7280000-f7283fff
  *-network DISABLED
       description: Ethernet interface
       product: I210 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: p3p1
       version: 03
       serial: d0:50:99:53:4f:e7
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=igb driverversion=5.0.5-k firmware=3.16, 0x800004d6 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:19 memory:f7100000-f717ffff ioport:c000(size=32) memory:f7180000-f7183fff
```
```
oscar@HTPC:~$ ifconfiglo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:747 errors:0 dropped:0 overruns:0 frame:0
          TX packets:747 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:225195 (225.1 KB)  TX bytes:225195 (225.1 KB)


p2p1      Link encap:Ethernet  HWaddr d0:50:99:53:4f:e6
          inet addr:192.168.1.252  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5530817 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1171981 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:8018837238 (8.0 GB)  TX bytes:98825929 (98.8 MB)
          Memory:f7200000-f7280000


virbr0    Link encap:Ethernet  HWaddr 0e:af:01:68:17:5b
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```
```
oscar@HTPC:~$ route -nKernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 p2p1
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0
```
```
oscar@HTPC:~$ sudo ethtool p2p1Settings for p2p1:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Supported pause frame use: Symmetric
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Advertised pause frame use: Symmetric
        Advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        MDI-X: on (auto)
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000007 (7)
                               drv probe link
        Link detected: yes
```
```
oscar@HTPC:~$ ethtool -i p2p1driver: igb
version: 5.0.5-k
firmware-version: 3.16, 0x800004d6
bus-info: 0000:03:00.0
supports-statistics: yes
supports-test: yes
supports-eeprom-access: yes
supports-register-dump: yes
supports-priv-flags: no
```

---

### Post by TheFu on 2015-02-07
You don't have a default route for non-LAN traffic. Any idea why not?
Also - I'm a little confused by the p2p1-stuff.  Is something funny happening there?

Is this a normal wifi-router connection to broadband with a few devices inside on the LAN side or is something non-standard happening like a vpn?

Here's my route:
```
$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         rt1             0.0.0.0         UG    0      0        0 eth0
172.22.22.0     *               255.255.255.0   U     0      0        0 eth0

```

---

### Post by Smokin Whale on 2015-02-08
I'm having exactly the same issue and also made a thread about this: [http://ubuntuforums.org/showthread.php?t=2264278](http://ubuntuforums.org/showthread.php?t=2264278)

Very annoying. I'm getting a little more performance than you but it's still unacceptable. I gather you're using Ubuntu 14.04 64bit?

---

### Post by Oscar Garza on 2015-02-10
I have no idea why it is set up like that, the box is connected to the router via ethernet cable, the p2p1 and p2p2 were the two ethernet ports on the motherboard, they were named like this when I installed the server, the virbox one appeared after installing virtualbox.

There's nothing too out of the ordinary on my set up though, I have an AP connected to the lan port of the router and the server is connected directly to the router via ethernet cable

---

### Post by Oscar Garza on 2015-02-10
[SIZE=1]Yes, 10.04 64 bit[/SIZE]

EDIT -- I'm on 14.04, 64 bit.. not 10.04

---

### Post by TheFu on 2015-02-10
a) time to migrate to a newer release. 12.04 or 14.04.  Support for 10.04 server ends in 2 months or so. 10.04 Desktop support ended 2 yrs ago.
b) disconnect the AP and reboot, if that fixes it, then it is a routing issue, as I suspect.  Without a default route, I'm amazed that anything works outside the LAN at all.

Refer to my example routing table above for what normal routing should look like. Of course, your gateway, IPs and subnet will be different.

It would also help to see the /etc/network/interfaces file. Please post it.

---

### Post by Oscar Garza on 2015-02-11
My mistake, I am on 14.04.

I'll try resetting.

This is the output of /etc/network/interfaces

```
oscar@HTPC:~$ sudo tail /etc/network/interfaces# The loopback network interface
auto lo p2p1
iface lo inet loopback


# The primary network interface
iface p2p1 inet static
        address 192.168.1.252
        netmask 255.255.255.0
        gateway 192.168.1.1
        dns-nameservers 8.8.8.8 8.8.4.4

```

192.168.1.1 is the router, the AP is 192.168.1.253

I have no idea why the output is now different, I just ran the route -n command again before changing anything and this is what it looks like right now:
```

oscar@HTPC:~$ sudo route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 p2p1
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 p2p1
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0

```

---

### Post by SeijiSensei on 2015-02-11
Is the AP just a simple "access point" or a router?  If the latter, why isn't that the default gateway?

---

### Post by TheFu on 2015-02-11
So - is it faster without the AP or not?  Need the info dude.

---

### Post by Oscar Garza on 2015-02-13
> **SeijiSensei said:**
> Is the AP just a simple "access point" or a router?  If the latter, why isn't that the default gateway?
It's a simple access point, an Engenius EAP600

---

### Post by Oscar Garza on 2015-02-13
> **TheFu said:**
> So - is it faster without the AP or not?  Need the info dude.
It's the same speed. The linux box does not have wireless, that's why it is connected directly to the router

---

