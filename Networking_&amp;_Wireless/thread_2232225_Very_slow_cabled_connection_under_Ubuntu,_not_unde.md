---
title: "Very slow cabled connection under Ubuntu, not under Windows"
date: 2014-06-30
forum: Networking &amp; Wireless
---

### Post by DaveCat on 2014-06-30
Hello!
I'm connected via LAN cable and connection is very slow under linux, but quite fast under windows.
Ethernet device name is eth0.
Thin being the problem, I post some outputs of general interest:
```

dave@psh:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:f3:ca:23:42  
          inet addr:172.16.1.67  Bcast:172.16.3.255  Mask:255.255.252.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8802 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4803 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5140381 (5.1 MB)  TX bytes:490807 (490.8 KB)
          Interrupt:45 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:48 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3744 (3.7 KB)  TX bytes:3744 (3.7 KB)

wlan0     Link encap:Ethernet  HWaddr c4:85:08:06:a0:0e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

```

dave@psh:~$ sudo lshw -class network
  *-network               
       description: Wireless interface
       product: Centrino Advanced-N 6235
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: mon.wlan0
       version: 24
       serial: c4:85:08:06:a0:0e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical wireless ethernet physical
       configuration: broadcast=yes driver=iwlwifi driverversion=3.13.0-30-generic firmware=18.168.6.1 ip=192.168.150.1 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:48 memory:f7d00000-f7d01fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.2
       bus info: pci@0000:03:00.2
       logical name: eth0
       version: 0a
       serial: 00:23:f3:ca:23:42
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.037.00-NAPI duplex=full ip=172.16.1.67 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:45 ioport:e000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff

```

```

dave@psh:~$ sudo ethtool eth0
Settings for eth0:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: Twisted Pair
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: Unknown
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00000033 (51)
                   drv probe ifdown ifup
    Link detected: yes


```

There are a few things I have already tryed:
- disabling ipv6
- changng DNS
- commented out "dns=dnsmasq" in /etc/NetworkManager/NetworkManager.conf
- something else I dont even remember now!

System is Ubuntu 14.04 LTS, installed a week ago or so.
Funny thing: downloaded ubuntu iso for installing it using windows, it took less than two minutes!

Thanks in advance!

---

### Post by DaveCat on 2014-06-30
I have experienced slow connection also in windows today, so it can be a problem of the network itself.
Still, it seems that Ubuntu is more likely to be slowed down than Windows (win was going fast in the beginning, but at some point slowed down, whether Ubuntu is always slow).
Probably this thread should be removed, as it might be not a software problem.

---

### Post by slonk on 2014-06-30
How do you measure "slow"?

If Windows is sometimes affected, too, the reason might be messed up routes in the Ethernet. Is that in a large organization? In New England?

---

### Post by DaveCat on 2014-07-01
About the measure, I used an online speedtest. 
Yes, it's a big lan, a student dorm (but not in New England!). 
Indeed it is probably a network problem, that's why i said this thread might be usless.  I started it because for some days it looked like only Linux was slow.

---

