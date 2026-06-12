---
title: "Network Manager cannot connect to wireless first"
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by nofrak on 2007-04-20
I used Feisty Fawn through alpha, beta, and now I've installed the release from scratch.  During the pre-release stages, it seemed like ndiswrapper and network manager (knetworkmanager, actually) were going to play nice, but it broke just in time to go gold.  Here's the deal:

I boot up with Ethernet connection.  NM connects and everything is fine.  If I unplug the Ethernet cord, NM will switch without complaining to a wireless network.  All well and good.

I boot up without Ethernet connection, I get the all-too-familiar stuck at 28% problem when I try to connect to a wireless network.  Connecting works fine with "sudo dhclient eth1"

This was a problem out of the box, so I don't think it's a problem due to a configuration I made.  I have commented out all interfaces in /etc/network/interfaces, ndiswrapper is installed properly.

First I want to know if other people are having this problem.  I haven't had any luck finding a bug for it, and I don't want to file a new one if it only applies to me.

Second, if you have any kind of solution, I'd love to hear it.

---

### Post by crazy_cat on 2007-04-20
yes, im having the same problem.  i can connect using dhclient, but not with network manager in gnome.  i can see the network in the gnome manager, and it even asks me to put in my WPA key.  but it wont connect that way.  

ive tried to connect with the gnome network manager both ways: with WPA/WEP keys and a completely unsecured connection.  i setup everything up according to the HOWTO.

---

