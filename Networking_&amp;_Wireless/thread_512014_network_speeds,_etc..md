---
title: "network speeds, etc."
date: 2007-07-28
forum: Networking &amp; Wireless
---

### Post by toddpedlar on 2007-07-28
Hi -

I've got an issue with a new PC and network speeds.  I've got it connected to a Netgear Gigabit hub, and when I do, it seems to fail miserably to stay connected to the internet.  If I instead connect it to the 10MB hub I also have, no problems.  

The network card is supposed to be a 10/100/1000 NIC, but it seems to choke when I 
give it the full juice.    What's more, the line coming into the lab is only 100Mb, not 1000... 

Is there something I need to check out vis a vis the driver, or ?

The manufacturer is supposedly Marvell Technology Group, and it's an integrated NIC 
on the motherboard (88E8056 phy).  

The driver according to lshw -C network is sky2 version 1.13.

Any help/suggestion is appreciated.

Todd

---

### Post by noob12 on 2007-07-29
With a slightly different Marvell chipset connecting to a Netgear GS105 V2 switch, had a problem with autonegotiation.  Fixed it by adding **pre-up** lines to /etc/network/interfaces to force 1000mbps full duplex using ethtool.

What does ethtool report on the negotiated link?

---

