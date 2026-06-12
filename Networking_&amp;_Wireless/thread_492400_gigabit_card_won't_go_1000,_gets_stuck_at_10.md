---
title: "gigabit card won't go 1000, gets stuck at 10"
date: 2007-07-04
forum: Networking &amp; Wireless
---

### Post by maybeway36 on 2007-07-04
I have a gigabit card in an Ubuntu 7.04 server. Last week I got the card to go from 100Mb/s to 1Gb/s by issuing the command
```
sudo ethtool -s eth1 speed 1000
```
and it worked for a few days until I took the server into another room to troubleshoot with a Knoppix disc. I then hooked up a 100Mb/s connection to make sure the server still worked. When I put it back in the room with a 1Gb/s connection, it was still 100Mb/s! I tried typing the above command, but then it went to 10Mb/s (even worse!) and wouldn't change until I rebooted.
Any ideas on what might help?

---

### Post by gangolli on 2007-07-22
I have had problems with my gigabit ethernet cards (Marvell chipsets in my case) not autonegotiating to 1000mpbs under Ubuntu.  I usually get stuck at 100, not 10 though.

Here's what I'm using as a workaround on my desktop, a stationary wired host. 

In the /etc/network/interfaces file find the section for the interface corresponding
to your card and add a line like the following after the "iface" line.  Be sure to replace eth0 with the
corresponding actual interface for your card.

> 
pre-up /usr/sbin/ethtool -s eth0 speed 1000 duplex full autoneg off


This will take effect the next time /sbin/ifup is run (next reboot or earlier if you force it down and up manually).
Note that this turns autonegotiation off.   So it assumes the card is hooked up to a gigabit-capable switch.

I'd be happy to hear of a solution that does not involve doing this.  I believe it is a bug in the driver's negotiation code, but that's just a hunch.

---

