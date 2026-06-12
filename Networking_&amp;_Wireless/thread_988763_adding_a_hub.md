---
title: "adding a hub"
date: 2008-11-20
forum: Networking &amp; Wireless
---

### Post by trinifar on 2008-11-20
I'm new at setting up LAN's and would appreciate some pointers.  Been reading a lot here and elsewhere but am clearly missing some key points.

I have two Ubuntu based systems (one Kubuntu, the other Xubuntu, both 8.04) that are connected to a broadband router, both have local static IP addresses assigned by the router (because I thought that would simplify things). The Kubuntu machine has a wired connection and the Xubuntu a wireless one.  I gave them host names and can ping one from the other.

Because I have another Linux machine and plans for more, I got a 4-port hub and have burned a lot of time trying to make things work.  Probably hopelessly naive.  

My goal is to have everything working through wired connections with wireless only as an option.  So I connected the uplink port on the hub to the router with a patch cable, then each of the two existing machines into the hub.  The hub looks happy; it's LED's blink appropriately.  But neither machine can see the LAN or the router or the Internet.

Where do I start?  What information can I provide that's useful for debugging?  I'd really like to learn how to do this thing that I thought would be so simple.

---

### Post by gpsmikey on 2008-11-20
If it is indeed a hub/switch, then they should all be able to see each other.  Start by checking the addresses on each machine (and the netmask).  They should all be in the same subnet as the router (which is probably 192.168.1.1 or 192.168.2.1).  It is not clear from your post how the machines got their addresses - you indicate they are static addresses, but were obtained from the router.  If they were obtained from the router, then they are dynamic (obtained via DHCP) although some routers allow you to hand out a known address to a particular machine each time (Tomato in my Linksys allows that handy feature).  Assuming a normal type configuration, I would expect to see the router with an address for example of 192.168.1.1 and the other machines would have addresses of 192.168.1.xxx where the "xxx" is between 2 and 254.  Typically the net mask would be 255.255.255.0 for this configuration.  You can check the machines with the command **[COLOR="Red"]ifconfig[/COLOR]** in a terminal window.  One possible trap door - if you have a switch in the middle, make sure you have either rebooted the machines connected to it or have cycled power on the switch - they can get confused when you move cables around and not be able to talk to the right port.

Let us know what you come up with and what addresses the machines are showing.

EDIT - just noticed you commented on a "patch cable" - the connection between the hub/switch and the router should be with a normal cable not a cross-over cable (although some switches/routers have auto-sense and can handle that).  The uplink port on the switch to the port on the router is just a regular ethernet cable.

mikey

---

### Post by trinifar on 2008-11-22
mikey,

Thanks for the quick reply.  New information:  Occurred to me that the hub might not be working properly and I discovered I had an old dual band access point that contained a four port switch.  So I replaced the hub with it and now I have connectivity on one computer and, for what it's worth, dual band wireless on my little subnet (if that's even the proper term). 

Tomorrow I'll see if I can make some more progress and post an update along with the information I've gather.  Now, however, it is time for sleep.

---

