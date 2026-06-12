---
title: "ethernet to wireless bridge, can only ping bridge, routing problem?"
date: 2007-02-24
forum: Networking &amp; Wireless
---

### Post by jsherman999 on 2007-02-24
I'm hoping this is actually an easy problem, possibly related to routing, vs. actually a wireless problem:

I have an Edgy box that I'd like to connect to my wireless network via a wireless-ethernet bridge - an SMCWEBT-G to be exact.

When Edgy is connected directly to the bridge with ethernet, I can ping the bridge, but nothing beyond it.  Same when Edgy and Bridge are both connected to a switch.

The bridge works, XP boxes connected to it as a test can see the rest of the network fine.

I'm thinking wireless shouldn't even be an issue here, since Edgy should just see itself as connecting with a regular old ethernet cable, right?  Is this a routing issue?

Here's the network - 192.168.2.0 is the wireless network, Modem at 192.168.0.1.

"WR" == Wireless Router below, ---e--- = ethernet, ...w... = wireless:  

(Edgy: .2.104) <--e--> (.2.25 Bridge)<......w.....>(.2.1 WR .0.12)<---e-->(modem 0.1)


netstat -r gives:

[FONT="Courier New"]Destination        Gateway             Genmasks             Flags
192.168.2.0       *                        255.255.255.0       U
default              192.168.2.1         0.0.0.0                  UG[/FONT]

As I said, I can ping the bridge at .2.25 from edgy, nothing beyond.

Is my routing set up right, or is there somehing else I need to do at the bridge or at Edgy to ge the traffic through the bridge?

Thank you very much in advance for any help you can provide.

---

### Post by gradedcheese on 2007-02-24
what does "route -n" say?  The bridge should be in there, as a gateway (as I understand it)

---

### Post by jsherman999 on 2007-02-24
'route -n' shows me nothing (except the header of course)

I'm assuming what shows up in 'netstat -r' as 'default' is the default route, right?  should I see  something more with route -n, and if I don't what's the cause/fix?


Thx!

---

### Post by gradedcheese on 2007-02-24
'route' shows the kernel's routing table, so I'd say it's a safe bet that you have no route to the gateway (bridge).  You should have a route similar to:

```

0.0.0.0         192.168.2.25     0.0.0.0         UG    0      0        0  eth0

```

...I think (that is, anything via eth0 goes through gateway 192.168.2.25).  You can add a route (run "man route" for instructions) and see if that helps.  I think it's something like:

```

sudo route add 192.168.2.25 gw

```

but I might be wrong.  You could also configure your network interface with a static IP and 192.168.2.25 as its gateway IP.  How does the PC get an IP now?

---

### Post by jsherman999 on 2007-02-24
Actually, I take that back - route -n does show the same thing as netstat -r, except 0.0.0.0 in place of the * for the gateway.

---

### Post by jsherman999 on 2007-02-24
I've configured it with both static IP and tried to use DHCP - right now I'm attempting to use a static IP (.2.104).

I have tried using 192.168.2.25 as the gateway in the interfaces file, as well as 192.168.2.1.  No luck with either.  It can always just ping .2.25.

I do see a route just like you show there, but with .2.1 as the gateway.  I'll try again to reconfigure with .2.25 as the gateway...

(BTW, thx for the help attempt, very speedy!)

---

### Post by gradedcheese on 2007-02-24
No problem.  I haven't used one of these bridge devices, so I am little confused.  Does the bridge do it's own routing?  Or is it literally a bridge... that is, do you think that DHCP requests from your PC will pass through the bridge, to the DHCP server on the other side, etc?  Does DHCP work?  Perhaps 192.168.2.1, in that case, really is the correct gateway (passing through the bridge).  However in that case you'd also be able to ping 192.168.2.1, so that's a bit odd.

---

