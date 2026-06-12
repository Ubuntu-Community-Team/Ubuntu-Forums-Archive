---
title: "Routing"
date: 2007-05-07
forum: Networking &amp; Wireless
---

### Post by Radomir on 2007-05-07
I'm not sure if this is an Ubuntu specific question, but I need help as I'm not sure how to do this...

I would like to setup an Ubuntu box (Intel Pentium D, Asus P5B-MX, two NIC's - one integrated and one Realtek 8139) as a router and a firewall. One NIC is connected to LAN, static configuration with a B class private address, 10.5.0.6, and other one is connected to my ISP, configured by DHCP. I have managed to setup IP masquerading from local network to internet, and have no problems with that, but I have a specific need - on my local network there is one router which routes trafic to other B class addresses - aka. I would like my Ubuntu 
box to route packages that come from local network and go to 10.0.0.0 netmask 255.0.0.0 to 10.5.0.1 router, 
and for other destinations  I would like masquerading. Basically, I need to route packages on same local interface. Is that possible? Any hint would be appreciated. 
I tried with route add 10.0.0.0 netmask 255.0.0.0 gw 10.5.0.1 dev eth0, and it works on router, but packages that come from local network to router are not routed to 10.5.0.1 and back. I had a similar situation on Windows 2003 box, and solved it by entering a static route. IP forwarding is enabled. Can this be done?
Regards.

---

### Post by Synflux on 2007-05-07
Hi,

I've only been using Ubuntu for a few days so I can't help with the specific commands but I think the problem may be in your subnet masks and I'm confused about what you're trying to achieve, are you saying that you want to end up with two routers on your lan? 

If so, what IP address is the other router? 10.5.0.1? That would make it in the same subnet as your Ubuntu box?

> **Radomir said:**
> 
I tried with route add 10.0.0.0 netmask 255.0.0.0 gw 10.5.0.1 dev eth0, and it works on router, but packages that come from local network to router are not routed to 10.5.0.1 and back.

That's a class A subnet mask rather than a class B, maybe this is where you're problem is?

> **Radomir said:**
>  I had a similar situation on Windows 2003 box, and solved it by entering a static route. 
If you've got two routers then you'll need to setup static routes on both of them, and they will need to be in different subnets.

I hope that helps, let me know if you need any more help with it. :)

---

### Post by Radomir on 2007-05-07
Well this is how it goes - the other router can not be touched for number of reasons, so I'm stuck with this...
Basically, I need it to work like this - two routers on same subnet, one is 10.5.0.1 and other one - Ubuntu box - is 10.5.0.6. What I would like to do is to tell my Ubuntu box to route all the packages that come in from local lan to 10.5.0.1 if their destination is 10.0.0.0.
#route add -net 10.0.0.0 netmask 255.0.0.0 gw 10.5.0.1 dev eth0
This works for Ubuntu box, but incoming packets are not routed. IP forwarding is enabled, and I'm not sure if Ubuntu can route packets on same interface. Windows RAS does this by adding static route in console. 
I know that two routes are not optimal solution, but it has to be done this way for now.
Btw,yes, it's A class network, but that is not the issue, at least I think so.

---

### Post by Synflux on 2007-05-08
Hi,

Okay, I think I know what you're asking now.  I don't know if you can forward out the same interface as the packets are received on if the destination is the same as that interface, it would assume that the packet has already reched it's destination and doesn't need to be forwarded anymore.

You say that your static route on the ubuntu box is working so all you need to do is add static routes on all the hosts (other computers on the lan) to forward 10.0.0.0/8 to 10.5.0.1 and 0.0.0.0 to 10.5.0.6 so they look to the Ubuntu for the internet but your other router for anything in 10.0.0.0. In other words, add the exact same static route to all other hosts.

As both your routers are in the same subnet you don't need to forward from your ubuntu box onto the other router, just use static routes on all the pc's to point to 10.5.0.1 for any traffic in the 10.0.0.0 subnet.

Does that make sense? It's too early in the morning for me! :confused:

---

### Post by Radomir on 2007-05-08
It does - but that's what I want to avoid. Then I would have to set static routes for all the machines that use this box as gateway. 
But, today I did a retest with Firestarter - needed simple Internet connection sharing, and voila! it is working!
I added this : route add -net 10.0.0.0 netmask 255.0.0.0 gw 10.5.0.1 and Ubuntu is routing traffic on the same interface. 
Dunno what was wrong? Anyway, thanks for help!
Regards.

---

