---
title: "r8169 Gigabit only connecting at 10Mb/s"
date: 2007-10-18
forum: Networking &amp; Wireless
---

### Post by cdpuk on 2007-10-18
Hi, basically the topic says it all.  I've been googling about for hours for a solution but nothing useful comes up.  I've tried the driver from the Realtek website but the same happens.  I've also tried another cable which connects fine to other gigabit NICs, but not this one - 10Mb/s again.

Here's some info that might help:

Kubuntu 7.10, Linux 2.6.22-14-generic

```
chris@hex:~$ lspci | grep RTL
01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)
```

```
chris@hex:~$ sudo ethtool eth0
[sudo] password for chris:
Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 10Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
        Link detected: yes
```

```
chris@hex:~$ dmesg |grep eth0
[   26.677187] eth0: RTL8169sc/8110sc at 0xffffc20000aac000, 00:19:21:35:36:3a, XID 18000000 IRQ 20
[   33.076562] r8169: eth0: link down
[   33.991266] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   67.220548] r8169: eth0: link up
[   67.224970] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   77.418939] eth0: no IPv6 routers present
```

Any help much appreciated,

-Chris

---

### Post by noob12 on 2007-10-18
Can you post the actual device id from **lspci -nn** ?

What rate is the port to which you are connecting (on the other side)?

You may be able to workaround autonegotiation failures by adding the following pre-up line to your /etc/network/interfaces stanza for eth0:
```

pre-up ethtool -s eth0 speed 1000 duplex full autoneg off

```

---

### Post by cdpuk on 2007-10-18
> **noob12 said:**
> Can you post the actual device id from **lspci -nn** ?

What rate is the port to which you are connecting (on the other side)?

You may be able to workaround autonegotiation failures by adding the following pre-up line to your /etc/network/interfaces stanza for eth0:
```

pre-up ethtool -s eth0 speed 1000 duplex full autoneg off

```

```
01:05.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet [10ec:8167] (rev 10)
```

On the other side is a Netgear GS605 Gigabit switch, working fine with other gigabit NICs.

I've tried a few ethtool commands to try and force it to 1Gb with no luck.  I'll try that pre-up one soon and post back.

Cheers,

-Chris

---

### Post by cdpuk on 2007-10-18
Unfortunately that prevented the network operating at all.  ethtool showed a 10Mb half duplex link again but I couldn't access anything over the network.

Any more ideas?

-Chris

---

### Post by noob12 on 2007-10-18
Also try with autoneg on i.e.:
```

sudo ethtool -s eth0 speed 1000 duplex full autoneg on

```
or the equivalent pre-up.

---

### Post by noob12 on 2007-10-18
Also try with autoneg on i.e.:
```

sudo ethtool -s eth0 speed 1000 duplex full autoneg on

```
or the equivalent pre-up.

You could also be having some more generic timing issue.  Are you seeing any errors in **tail /var/log/kern.log** ?

---

### Post by cdpuk on 2007-10-19
> **noob12 said:**
> Also try with autoneg on i.e.:
```

sudo ethtool -s eth0 speed 1000 duplex full autoneg on

```
or the equivalent pre-up.

You could also be having some more generic timing issue.  Are you seeing any errors in **tail /var/log/kern.log** ?

That command doesn't seem to make any difference, it stays at 10Mb, but the network connection still works.

kern.log only contained two lines corresponding to the interface going down then back up after what I assume to be the ethtool command.

-Chris

---

### Post by noob12 on 2007-10-19
All I can suggest is checking the BIOS for any settings related to this and the physical connection.  Check the RJ-45 port for dust and that each of the leads is springing up to make full contact with the jack.  Try swapping the cable even though you said it worked for other NICs.  

File a bug on launchpad  [https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)

---

### Post by Chalzor on 2007-11-07
I am having this problem too, on 2 different systems both with 3 rtl8169 nics. Running Feisty,  

uname -a shows:

Linux hydra1 2.6.20-16-server #2 SMP Sun Sep 23 19:57:25 UTC 2007 i686 GNU/Linux

lspci -nn lists 

00:0e.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet [10ec:8169] (rev 10)
00:0f.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet [10ec:8169] (rev 10)
00:10.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet [10ec:8169] (rev 10)

Weirdness is 1 nic on each box, connected via crossover links at 1000, the rest I get linking at 10 when plugged into a Gigabit port,  tried 3 different brands of gigabit switches - netgear(5 port), smc(8 port), airliink(8 port).  Also tried changing cables from cat5e to cat6, no difference.

When plugged into a 100Mbit switch they come up at 100.

Tried the r8168 module off realtek's site, but it did not even detect the cards. 

I am trying to build up a redundant NAS using ubuntu,  everything is working but I cannot get it to connect at gigabit speeds through the switches.

Ive tried forcing it with ethtool to no avail....

Any suggestions?

Chalzor

---

