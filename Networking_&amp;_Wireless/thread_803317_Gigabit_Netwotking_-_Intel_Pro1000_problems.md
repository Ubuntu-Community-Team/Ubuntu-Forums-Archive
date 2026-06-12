---
title: "Gigabit Netwotking - Intel Pro/1000 problems"
date: 2008-05-22
forum: Networking &amp; Wireless
---

### Post by drsox1899 on 2008-05-22
I have several problems with my network config that may just be due to my not being able to find the right Ubuntu documentation, so please point me to the right info if it is there.  I'm running 7.10.

1. I have standardised on Intel Pro/1000 MT NICs BUT when they boot up they always seem to run in 100mbps mode.

From mii-tool I get : 

	eth3: negotiated 100baseTx-FD flow-control, link ok
	

From ethtool eth3 I get :

 	Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: umbg
        Wake-on: g
        Current message level: 0x00000007 (7)
        Link detected: yes

What do I do to get a permanent 1000Mb/s connection ?
Do I turn off auto-negotiation ? and HowTo ?
Do I set them to AutoFullDuplex ? and HowTo ?

I have tried using : 

	sudo ethtool -s eth3 autoneg off speed 1000 duplex full

This changes the mii-tool output for eth3 to :  negotiated flow-control, link ok
This seems to have a temporary effect.

2. I also want them to run in JumboFrame mode with mtu=9000.

From my /etc/network/interfaces file :


	auto lo
	iface lo inet loopback



No mention of eth3.

If I add :

	auto eth3
	iface eth3 inet dhcp
	up ifconfig eth3 mtu 9000

It doesn't stick as the next time I boot up it is gone.

How do I get a permanent mtu 9000 ?

3. I get pulsing in my network transfers. 

The data rate cycles on a per second rate from 19MB/s to Zero in a sine wave.  
Even if I do simultaneous send and receive, both PCs show the same sine wave of send & receive at 19MB/s to Zero IN PHASE !

Is this related to an out of date Intel driver ? 
In U7.10 (and 8.04) the Intel driver is V7.3.20-k2-NAPI.
The latest SourceForge driver is V8.0.1.

Is this related to the lack of 1000Mb/s data rate and/or the JumboFrames ?

How do I get a continuous data transfer or is this normal behaviour ?



Thanks

---

### Post by drsox1899 on 2008-05-22
Repeat.

Typo Corrected !

---

### Post by drsox1899 on 2008-05-23
Repeat

---

### Post by Eric the Red on 2008-06-15
Bump!

---

### Post by atoponce on 2008-09-18
> **drsox1899 said:**
> 3. I get pulsing in my network transfers. 

The data rate cycles on a per second rate from 19MB/s to Zero in a sine wave.  
Even if I do simultaneous send and receive, both PCs show the same sine wave of send & receive at 19MB/s to Zero IN PHASE !

I too am noticing the sinusoidal networking behavior as is a coworker of mine.  We both have T61 laptops with the Intel gigabit NIC.  Any info in this would be appreciated.  It does not happen on Fedora, Arch Linux, or any other distro except Ubuntu.

---

