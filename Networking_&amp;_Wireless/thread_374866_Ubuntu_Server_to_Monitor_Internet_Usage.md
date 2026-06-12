---
title: "Ubuntu Server to Monitor Internet Usage"
date: 2007-03-03
forum: Networking &amp; Wireless
---

### Post by Tumbot on 2007-03-03
Hello Bipeds,

Please help me.

I would like to start sharing my wireless hotspot with my neighbors.  However I want to have control over their use of my Internet connection.  The problem is that the wireless router through which we will all connect to each other is also the connection to the Internet.
I would like their computers to pass Internet requests through the router and to my computer, where my computer will then pass the request back to the router.

I have managed so far to disable any Internet requests that don't come from my computer from working on the router.  Now I would like to set up my computer as a DHCP server that shares its Internet Connection.  I'd like to know firstly whether it is possible to set up such a thing with only one network card and router.  And secondly if anybody has any clue as to how to do it.

Thanks in advance for any help
Tumbot

---

### Post by Mr. C. on 2007-03-03
I do not believe you will be able to do this with any commodity wireless access point/home router.

What you want is an access point (which you have) connected to a system that does routing, firewalling, and QoS.  Unless you can afford big hardware, you'll need a cheap system with a couple of Ethernet cards (one going out to your WAN (eg. your broadband) and one going to your LAN (your computer, access point, printers, etc.).

You can configure one of the many software routing firewalls (smoothwall, for example), and configure it to do what you like.  You can add a third Ethernet card if you want, and place your AP in a DMZ, so your neighbors have no access to your system.

Something to note: QoS only works for *outbound* traffic. You cannot control inbound.

---

