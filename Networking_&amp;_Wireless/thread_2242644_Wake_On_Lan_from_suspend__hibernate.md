---
title: "Wake On Lan from suspend / hibernate"
date: 2014-09-03
forum: Networking &amp; Wireless
---

### Post by samuelsson.joel on 2014-09-03
Hi,

I can't seem to get WoL to work from suspend / hibernate. It works fine if I shutdown my computer.

I've tried all sorts of guides:
[http://jerjou.blogspot.se/2010/10/wake-on-lan-from-suspend-in-ubuntu-1004.html](http://jerjou.blogspot.se/2010/10/wake-on-lan-from-suspend-in-ubuntu-1004.html) - does not work, my network card is already listed as enabled
[http://ubuntuforums.org/showthread.php?t=1642272](http://ubuntuforums.org/showthread.php?t=1642272) - does not work, no difference from before.
and several others to no avail.


```

joel@joel-laptop:~$ uname -a
Linux joel-laptop 3.0.0-12-generic-pae #20-Ubuntu SMP Fri Oct 7 16:37:17 UTC 2011 i686 i686 i386 GNU/Linux

```

```
joel@joel-laptop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.1 LTS
Release:    12.04
Codename:    precise

```


Any Ideas?

---

### Post by weatherman2 on 2014-09-03
What is your network card?  What's the result of

```
lspci -nn
```

and

```
sudo lshw -C network
```

and (assuming your network card is eth0, replace below if otherwise):

```
sudo ethtool eth0
```

---

### Post by samuelsson.joel on 2014-09-04
> **weatherman2 said:**
> What is your network card?  What's the result of

```
joel@joel-laptop:~$ lspci -nn
00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)

```

```
joel@joel-laptop:~$ sudo lshw -C network
  *-network               
       beskrivning: Ethernet interface
       produkt: 82579LM Gigabit Network Connection
       tillverkare: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logiskt namn: eth0
       version: 04
       serienummer: f0:de:f1:4e:ce:ef
       storlek: 1Gbit/s
       kapacitet: 1Gbit/s
       bredd: 32 bits
       klocka: 33MHz
       förmågor: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       konfiguration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.3.10-k2 duplex=full firmware=0.13-3 ip=192.168.0.193 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resurser: irq:40 memory:d2600000-d261ffff memory:d262b000-d262bfff ioport:5080(storlek=32)
```

```
joel@joel-laptop:~$ sudo ethtool eth0
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
    Speed: 1000Mb/s
    Duplex: Full
    Port: Twisted Pair
    PHYAD: 2
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: on
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00000001 (1)
                   drv
    Link detected: yes
```


Sorry for the swedish. I hope you still understand.

---

### Post by weatherman2 on 2014-09-04
It looks like you haven't installed the latest kernel updates in a long time.  Have you considered doing that?  You might get an updated driver for the e1000e driver used for your network card.  You might also be able to download the driver directly from here and build it:

[http://sourceforge.net/projects/e1000/](http://sourceforge.net/projects/e1000/)

---

