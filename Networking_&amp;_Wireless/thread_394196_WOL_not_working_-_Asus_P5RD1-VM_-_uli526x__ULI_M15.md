---
title: "WOL not working - Asus P5RD1-VM - uli526x / ULI M1573"
date: 2007-03-26
forum: Networking &amp; Wireless
---

### Post by LanceRushing on 2007-03-26
I have a Asus P5RD1-VM Mother board with an integrated NIC 

I am trying to get WOL to work. (I've tried on Dapper and Feisty Beta)

```
# sudo ethtool eth0
Settings for eth0:
        Supported ports: [ MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 1
        Transceiver: external
        Auto-negotiation: on
        Supports Wake-on: pg
        Wake-on: d
        Link detected: yes

```

Looks promising but:
```
# sudo ethtool -s eth0 wol pg
Cannot set new wake-on-lan settings: Operation not supported
  not setting wol
```

grrrr...

Let's check which module is being used:

```
# sudo ethtool -i eth0
driver: uli526x
version: 0.9.3
firmware-version:
bus-info: 0000:00:1b.0
```

Hmm, maybe uli526x supports an enable_wol option.  I tried: "options uli526x enable_wol=1" and then "options uli526x gobal_enable_wol=1"  (ala [http://ubuntuforums.org/showthread.php?t=318586](http://ubuntuforums.org/showthread.php?t=318586) ).  But got "uli526x: Unknown parameter `(global_)enable_wol'" in both cases.


Here is the lspci and lshw:

```
# sudo lspci
0000:00:00.0 Host bridge: ATI Technologies Inc: Unknown device 5a33 (rev 01)
0000:00:01.0 PCI bridge: ATI Technologies Inc: Unknown device 5a3f
0000:00:19.0 PCI bridge: ALi Corporation M5249 HTT to PCI Bridge
0000:00:1b.0 Ethernet controller: ALi Corporation M5263 Ethernet Controller (rev 50)
0000:00:1c.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
0000:00:1c.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
0000:00:1c.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
0000:00:1c.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
0000:00:1d.0 0403: ALi Corporation High Definition Audio/AC'97 Host Controller
0000:00:1e.0 ISA bridge: ALi Corporation PCI to LPC Controller (rev 31)
0000:00:1e.1 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
0000:00:1f.0 IDE interface: ALi Corporation M5229 IDE (rev c7)
0000:00:1f.1 RAID bus controller: ALi Corporation ULi 5287 SATA (rev 02)
0000:01:05.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5a61

```

```
# sudo lshw -C network
  *-network
       description: Ethernet interface
       product: M5263 Ethernet Controller
       vendor: ALi Corporation
       physical id: 1b
       bus info: pci@00:1b.0
       logical name: eth0
       version: 50
       serial: 00:11:22:33:44:55
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=uli526x driverversion=0.9.3 duplex=full ip=192.168.1.60 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:e800-e8ff iomemory:dffffc00-dffffcff irq:225

```


Any ideas?

-Lance ](*,) ](*,) ](*,)

---

### Post by majoridiot on 2007-03-26
try using **sudo** for your ethtool commands...

---

### Post by LanceRushing on 2007-03-27
Actually, all the commands are already sudo'd (notice the #).  I did a sudo -s before I started.

But it might be it be confusing for people, so I'll edit the first post.

-Lance

---

### Post by brunobelo on 2007-07-21
So, have you found the answer? I have the same board and the exact same problem. :-\

---

### Post by mattoramius on 2007-10-18
Someone has the answare. I got the same card and can't use wol.

thanks,

M.

---

### Post by LanceRushing on 2007-10-25
Still not working for me, but I haven't tried Gutsy yet.

To work around, I just put in an old NetGear card I had laying around.  The netgear worked fine.

-Lance

---

