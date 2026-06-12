---
title: "Want Creative Solution: Wireless Card/VMWare"
date: 2007-07-04
forum: Networking &amp; Wireless
---

### Post by lawtech on 2007-07-04
There are about a thousand ways to solve the following problem. I'm looking for one that (a) "just works", (b) is cheap, (c) is very easy, and (d) will come up in very little time. Please put on your thinking caps.

Basic Problem

I need to VNC into a virtual machine running in VMWare Server, through a wireless connection on the host.

Situation

I have a fresh Feisty install, fully updated, hosted on an Intel D865GBFL motherboard, with 2GB RAM and disk space to burn. There is a D-Link DWL-G510 wireless card installed in addition to the 10/100 Ethernet on the motherboard. A Netgear WGT624 v2 wireless firewall router is connected to a cable modem.

The host communicates just fine to the Internet using either the motherboard Ethernet (wired) or the wireless card.

I have a fresh VMWare server installed in Feisty via Synaptic, running a virtual machine containing a fully licensed, fully updated Windows XP.

I need access via VNC (TightVNC is the one in use) to the XP VM from anywhere on the net. Simple, right? Just bridge the XP VM to the router and open some ports.

Discussion

And that works. If I set VMWare to _bridge_ the XP VM to the (wired) Ethernet, the XP VM accepts the IP address and ports I've assigned to it in the Netgear router, and I can run TightVNC from anywhere and access the XP VM just fine.

If I set VMWare to _NAT_ the XP VM, the router can't open ports to the XP VM's actual IP address, because VMWare sets up a different subnet, and the router can't deal with that.

If I down the (wired) Ethernet and enable the wireless connection, then try to _bridge_, VMWare tells me (after some digging) that the path I'm using to the Internet does not fully implement the Ethernet standard, and therefore the bridge connection cannot be set up.

So why don't I just use the wired Ethernet connection? My wife. There is a 100-foot Ethernet cable running between the Netgear router and the place where this box HAS to be. And that cable HAS to go! Now! For cheap!

As I said above, there are about a thousand solutions to this problem. Change to a different wireless card. (Which one?) Get this wireless card working to VMWare's satisfaction. (How?) Run bridge-utils to hook the VMWare NAT subnet to the wireless card. (Seems hard.) Find a cheap box that can talk wirelessly to the router and has a Ethernet port that I can wire to the one on the motherboard. (Is there such a thing?) And many others.

Every one of the solutions I've thought about seems to have one or more issues, cost, experimentation requirements, complexity, etc., etc. What I want to know is this:

Is there an obvious solution I'm apparently not seeing?

What is the solution that best meets the criteria in my lead sentence at the top of this page?

Thanks.

---

### Post by samexner on 2007-07-04
i want that kind of card too

---

