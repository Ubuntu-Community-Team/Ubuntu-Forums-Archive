---
title: "Wireless card cause lockup"
date: 2008-01-19
forum: Networking &amp; Wireless
---

### Post by ubumagic on 2008-01-19
Just after connecting to the net for few seconds it freezes up the machine.

N/w card is trendnet TEW-423 PI. Works great on XP.
Fiest Fawn 7.04
ndiswrapper is 1.48

Is there something i can run to diagnose to find whats going wrong on my box ?  Need help on this one.  Trying to fix this since oct 07

---

### Post by texasjim on 2008-01-19
What is the chipset on your card?  I have a similar problem with an Airlink 101 AWLH6045 adapter with the Marvell topdog chipset using ndiswrapper.

---

### Post by ubumagic on 2008-01-19
how do i find he chipset on the card ?

---

### Post by ubumagic on 2008-01-20
Network adapter is **RealTek RTL8185 54M Wireless LAN Network Adapter**

---

### Post by texasjim on 2008-01-21
> **ubumagic said:**
> Network adapter is **RealTek RTL8185 54M Wireless LAN Network Adapter**
I got mine to work on Gutsy by installing WICD from the Sorceforge web site.  There are flavors for Feisty and Gutsy available, WICD replaces  gnome-network-manager and/or KWLAN. Check your /etc/network/interfaces file, it is probably as cluttered wit stuff you have been trying as mine was. WICD has you clean the file to only 2 lines about your loopback interface, then creates the rest when you install it. Go to
 [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/) and I hope it goes as well for you.

---

