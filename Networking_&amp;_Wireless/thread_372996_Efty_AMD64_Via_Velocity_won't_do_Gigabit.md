---
title: "Efty AMD64 Via Velocity won't do Gigabit"
date: 2007-02-28
forum: Networking &amp; Wireless
---

### Post by m0bilitee on 2007-02-28
Hi folks - I've got a clean install (or it was until much apt-get'in ;-) ) of Efty Edge, AMD64 version.  My NIC is an onboard Via Velocity. The board is an Abit KV8-Pro, Athlon 3000+.  Dual booting into that *other* operating system gives me gigabit.  Under Ubuntu, however, I'm stuck in 10/100 land (and running at 100).

lspci says this:

00:0e.0 Ethernet controller: VIA Technologies, Inc. VT6120/VT6121/VT6122 Gigabit Ethernet Adapter (rev 11)


The system auto-detected via_velocity and uses that module so it shows up in lsmod.

Here's where things get strange.  If I run ethtool, here's my output:

Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Half 1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  Not reported
        Advertised auto-negotiation: No
        Speed: 100Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: puag
        Wake-on: g
        Current message level: 0x00000002 (2)
        Link detected: no

No link detected. Strange, I seem to be typing in a message on ubuntuforums.org. *big grin*

I can't get the thing to do gigabit, even though it should.  Ideas?

BTW, I grabbed the latest Via drives from viaarena.com and built those, same results.  

Surely someone has seen this before? Thanks in advance.  Help me not dual boot for net performance.  :-)

---

### Post by m0bilitee on 2007-03-01
Answering my own post--

I believe Ethtool lies.  :-)

According to my switch, I'm in 1000BaseTX mode, and the performance is just dandy (I didn't do any real testing, just was relying on what ethtool told me).

Interestingly enough, if I disconnect the cable from the Nic, Ethtool says "Link detect: yes".  Methinks ethtool and the via_velocity driver don't play nice.

---

