---
title: "D-Link ethernet card will not work full duplex"
date: 2006-08-11
forum: Networking &amp; Wireless
---

### Post by perez-franco on 2006-08-11
Personal Info aka The Sad Story

Hi there. My name is Roberto Perez-Franco. I am a 30 years old engineer from Panama. Soon I will return to MIT for a PhD. My father, who is 67, bought a computer to stay in-thouch with me while I am away. It is very important for me to help him have a safe, stable platform for accessing the Internet. I discarded Windows because it is too prone to malware, virus, spyware and all kinds of garbage that assault your PC as soon as you connect to the Internet. So, I decided to install Ubuntu in my father's PC, because he is not very tech-savy. I like Ubuntu so much that I want to use it myself when I return to MIT this Fall. However, Ubuntu has not performed as I would like in my father's PC. Among other things, we have been unable to get his network card to work correctly. In my town in Panama there are not many choices of network cards: the best we found was a D-Link that is only running half duplex. :( 

Problem description

I am running Ubuntu 6. My network card is a D-Link DFE-520TX. Ubuntu recognizes the card when I install it, and allows me to browse the Internet, albeit at a third of the normal connection speed. Our home connection is through a LAN cable, which connects to a radio (e.g. a connection via radio-antena to a distant provider located in a hill) with a speed of 128kbps. I have verified the speed repeatedly with my laptop, which is also running Ubuntu 6, and the connection effectively reaches 128kbps in the laptop, but not in the desktop. The D-Link card in the desktop only allows us to connect at around 40kpbs. When I run mii-tool, it reports that the card was able to negotiate 10baseT-HD. I would like to take it to full duplex to see if this allows us to navigate at the full speed of our connection.

The network card came with a CD, which includes a TAR file with half a dozen files which can be used to 'compile' the driver for this network card for use in linux kernel 2.6.

My questions are:
- Have you or anybody you love suffered a similar problem in the past?
- If so, how was it solved?
- Will compiling the driver from the CD allow me to reach full duplex?

(In the meantime, I am learning how to compile the driver, and downloading, in my super-slow connection, the linux kernel).

Roberto

---

### Post by NetworkGuy on 2006-08-12
I'mnot sure that the duplex problem you are reporting is the problem.  If you are only running at 128K, then even 10Mbits at half duplex should allow you to communicate at 128K.  

I'm thinking that your problem is the actual desktop.  Is it possible you might have some sort of BIOS issue that isn't allowing the card to function fully?  Not sure what else it could be.

---

### Post by perez-franco on 2006-08-12
Maybe, but consider this: a friend of mine let me try an old network card he found in a box, a Compaq I think, and it's working perfectly. It's downloading at 110KB now, with everything the same, just changing the card.

---

### Post by NetworkGuy on 2006-08-12
If that older card is working OK, my guess is either the actual card has a defect or the BIOS can't handle that new card.  

How old is your desktop PC?

---

### Post by RedBoot on 2006-08-12
A quick look on line shows that, although there are some places that sell the DFE-520TX, the D-Link site itself doesn't even list it. There's a 528 that's not supported in the US and a 500 that's out of life cycle. Possibly you could return the NIC and just use the old card? 
The Ubuntu [supported NIC page ]("https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards")does list the DFE-530TX+ which just uses the common Realtek driver. Perhaps this card is available?

---

### Post by perez-franco on 2006-08-13
> **NetworkGuy said:**
> If that older card is working OK, my guess is either the actual card has a defect or the BIOS can't handle that new card.  

How old is your desktop PC?

My PC is new. I bought it two months ago.

---

### Post by perez-franco on 2006-08-13
> **RedBoot said:**
> A quick look on line shows that, although there are some places that sell the DFE-520TX, the D-Link site itself doesn't even list it. There's a 528 that's not supported in the US and a 500 that's out of life cycle. Possibly you could return the NIC and just use the old card? 
The Ubuntu [supported NIC page ]("https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards")does list the DFE-530TX+ which just uses the common Realtek driver. Perhaps this card is available?

I would stick by the old card, yes. But I wonder whether it will "break down" any time soon. My friend found it in a shoebox, because it was stored away, but it works wonderfully.

The problem with buying a new card is that I am now in the countryside of a third world country: the only cards available are one that doesn't work and one that works slow.

I guess I'll stick by the old one while I learn how to compile the drivers for the new ones.

Roberto

---

### Post by RedBoot on 2006-08-13
> I guess I'll stick by the old one while I learn how to compile the drivers for the new ones.
Perez-Franco,
I hope to hear that this works for you. I live in the U.S., but help a rural town in Guatemala with Ubuntu. We have to use whatever we can get there, too. I would like to know if compiling the driver works.

Buena suerte!
Scott

---

### Post by profdreamer on 2006-10-17
Not sure if this will help, but I just bought and installed the very same card and was amazed to discover that it used the same Ubuntu driver as my previous LAN (onboard) chip. No compiling or installation required. The driver's "via-rhine", included in the Breezy kernel. 

Perhaps loading via-rhine (sudo modprobe via-rhine) will do the trick. You could try removing the driver currently being loaded first (sudo modprobe -r name_of_driver)..

Good luck! :)

---

### Post by mips on 2006-10-17
Does your laptop run FD or HD ? It might be that the device on the other end of the cable does not support FD.

Try ethtool, mii-tool does not work for me.

**_mii-tool:_**
Options are- 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD
**sudo mii-tool -F 100baseTx-FD eth0** would set the card to 100Mb/s Full-Duplex

**_ethtool:_**
Options are-
-s DEVNAME \
                [ speed 10|100|1000 ] \
                [ duplex half|full ]    \
                [ port tp|aui|bnc|mii|fibre ] \
                [ autoneg on|off ] \
                [ phyad %d ] \
                [ xcvr internal|external ] \
                [ wol p|u|m|b|a|g|s|d... ] \
                [ sopass %x:%x:%x:%x:%x:%x ] \
                [ msglvl %d ]

[B]sudo ethtool -s eth0 speed 1000
sudo ethtool -s eth0 duplex full[/B]

---

