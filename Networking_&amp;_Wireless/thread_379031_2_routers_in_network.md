---
title: "2 routers in network"
date: 2007-03-08
forum: Networking &amp; Wireless
---

### Post by tjtansey on 2007-03-08
Ok I know that this doesn't exactly apply here, but I'm the one saddled with making this work.  I just hooked another wireless router to the main modem/router in the house.  The new one is a Linksys WRT54GS and the existing one is a Linksys cable modem/wireless router.  How do I set router 2 up so that the computers connected to it can a) share printers with computers on router/modem. (lpstat sees the printer, but the testpage gets stuck in the queue and never prints.) b) being able to share files between computers reguardless of which router they are hooked to.  
Like I said, I know this is beyond the scope of this forum, but the knowledge base is here and I haven't been let down yet.
Thanks

---

### Post by Mr. C. on 2007-03-08
Let's make sure the details are clear.

You have a cable modem (CM), that now has two wireless routers (W1 and W2) connected to CM via Ethernet cables?

MrC

---

### Post by Sammi on 2007-03-08
According to my very limited knowledge, only one should have DHCP enabled.

---

### Post by Mr. C. on 2007-03-08
> **Sammi said:**
> According to my very limited knowledge, only one should have DHCP enabled.

There can be any number of DHCP servers on a LAN.  The requirement is they do not use overlapping IP ranges.  The first server to respond, and who's offer is accepted by the client, wins.

MrC

---

### Post by tjtansey on 2007-03-08
Router 1 is a cable modem/wireless router.  It has 2 problems:  
1.  Limited wireless coverage due to location (no it can't be moved)
2.  It is limited to 5 IP addresses.

The shared printer is connected to the one computer hard wired to that router.

Router 2 is a Linksys WRT54GS router located on another floor of the house (and 75' of network cable away).

My computer when connected to router 2 detects the printer when i run lpstat from the terminal, but will not print.  Obviously the computers hooked to router 2 can share files and the computers hooked to router 1 can share files.

So what I want to do if possible is:
1. be able to print network wide (I know this is possible but how?)
2.  Be able to share files network wide.
3. Not be limited in the # of available IP addresses, which I currently am not as long as connected to router 2.

I'd love to have all 3 choices, will be satisfied with choices 1 and 3 but must have choice 3 not matter what, or having the second router is pointless.

I hope that clears the question up.

---

### Post by Mr. C. on 2007-03-08
Ok, I think I have it.  I am assuming, as it wasn't mentioned specifically, that you *do* have a (75 foot length of) cable between R1(modem/router) and R2(Linksys).

So, the answer to your questions, yes, yes, and yes.... but, you need an extra piece of hardware IF your R1 router does not allow you to configure a route (and I doubt it does).

The problem is this.  R1 only knows how to send to either a) your 5 IPs, or b) the rest of the world.  It can only do one of those.  Because of that, there is no way to get traffic from R1 to systems hidden behind R2.

What you do need, and this solve all the problems, is another cheap router.  You will connect this between R1 and PC1, and connect the cable from R2 to one of the new router's LAN ports.  The WAN port of the new router goes to R1.  R1 then only sees two IP addresses, those of R1 and R2.  Configuring R1 and R2 is trivial.

If you want to go that route (sorry, pun), let's talk more.

MrC

---

### Post by cantormath on 2007-03-08
if you cascade the two routers, you can plug modem to router 1, then attach a cable from router 1, pluged into anyone of the four or whatever jacks in the back, to the internet jack of router 2. Change the subnet on router 2.
ie) if router 1 is 192.168.1.1
then change the ip (starting from) to 192.168.0.1, or whatever.  That should work.
This is one of many ways.

If they are both wireless routers, and the right kind, you could use dd-wrt firmware, which would make things alot easier turning router two into a access point.....

---

### Post by tjtansey on 2007-03-08
You were right on the assumption of 75' of cable.  Router 1 does have port forwarding if that makes a difference I also can forward the config pages on to you if that helps.  The subnet mask is set and I can find no way to change it.  It is set to 255.255.254.0.  Of course on the other router I can do whatever I want.  The piece of the puzzle I left off is this; router 1 also serves a computer at one end of the house.  Before you ask, it's an old house with brick walls on the first floor which of course kills the signal from router 1.  If it's at all possible we'd prefer not to add a switch, but if need be, I'll see what the decision is.

---

### Post by Mr. C. on 2007-03-08
> **cantormath said:**
> if you cascade the two routers, you can plug modem to router 1...

Ummm, the OP said modem and router 1 are the same piece of hardware.

---

### Post by Mr. C. on 2007-03-08
> **tjtansey said:**
> You were right on the assumption of 75' of cable.  Router 1 does have port forwarding if that makes a difference I also can forward the config pages on to you if that helps.  The subnet mask is set and I can find no way to change it.  It is set to 255.255.254.0.  Of course on the other router I can do whatever I want.  The piece of the puzzle I left off is this; router 1 also serves a computer at one end of the house.  Before you ask, it's an old house with brick walls on the first floor which of course kills the signal from router 1.  If it's at all possible we'd prefer not to add a switch, but if need be, I'll see what the decision is.

Ok, good on the cable.  If you want to PM me the pages, I'll take a look and see what options you'll have.  Forwarding won't affect anything, unless you want to access to your systems from the Internet.

How are your 5 IPs limited ?  Statically, or via their DHCP or PPPoE?  MAC addreses?

MrC

---

### Post by tjtansey on 2007-03-08
IP address for router 1 is 192.168.0.1 subnet mask is 255.255.254.0
router 2 is 192,168.1.1 s/m 255.255.255.0

cable is connected from rt1 lan to rt2 wan.

If I change the subnet on router 2 to 255.255.0.0 will that fix the issue?

---

### Post by Mr. C. on 2007-03-08
All network addresses on the same physical network must have the same subnet mask.

Your subnet mask on R1 is 255.255.254.0.  This is 510 hosts worth, and your network is 192.168.0.0/23.  Use the same subnet mask on all interfaces that connect to R1's LAN ports.

This is part of the connectivity problem.

I would still like to know how they limit your IPs... this will affect the solution.
MrC

---

