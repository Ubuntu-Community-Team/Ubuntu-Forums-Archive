---
title: "network manager pptp route?"
date: 2007-05-23
forum: Networking &amp; Wireless
---

### Post by jdbausch on 2007-05-23
I'm new to ubuntu, and I've been having a hard time finding an answer on this PPTP vpn stuff - so if this is shown somewhere else, I'm sorry up front, because I can't find it...

so here is the situation:
I've got a pptp vpn setup in network manger to the office firewall

it connects fine, but only allows access to the internal address of the Gateway  (we'll call that 10.0.0.1)

I can not ping anything else on that network.  Except for one magical afternoon where it just worked!  (actually it worked serveral times, as I rebooted and reconnected several times to test...)

anyway I'm not sure why it worked for that little while, as it normally does not work

so I figured out that I could manually add the route for the work network and it would work...


route add -net  10.0.0.0 netmask 255.255.255.0 dev ppp0

I can then access stuff on the work network...

however, since the work network's DNS server is 10.0.0.139, and I have to manually add a route, I can't use the DNS on the work network, so this workaround is both annoying and difficult to use


so here are my routes when the vpn connects:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
**10.0.0.1     *               255.255.255.255 UH    0      0        0 ppp0**
<PUBLIC IP>  10.1.2.1        255.255.255.255 UGH   0      0        0 eth0
10.1.2.0        *               255.255.255.0   U     0      0        0 eth0
default         10.1.2.1        0.0.0.0         UG    0      0        0 eth0


(10.1.2.1 is my home netowork)


my question is this:

how do I make the network manger pptp vpn setup the proper route as opposed to the bolded one shown above (which only allows access to the gateway)?

I'm hoping to have this just work by enabling the work vpn from network manager, and not need to run any scripts, etc


thanks

---

### Post by jdbausch on 2007-05-23
answering my on question...

I added that route, as described, and it sticks (I didn't know that it would last past a reboot)

so as long as the pptp config says to user peer dns, it looks OK

(at least during my lunch time tests!)

question still remains, how do you specify this in the network manager interface, or can you?

---

### Post by jdbausch on 2007-05-23
I come home again after lunch, try again, and my route is gone, even though no changes were made.  now I'm completely confused - help?

---

### Post by jdbausch on 2007-05-24
not that anyone cares, since I appear to be the only one reading or responding, but I found this page

[http://pptpclient.sourceforge.net/routing.phtml#client-to-lan](http://pptpclient.sourceforge.net/routing.phtml#client-to-lan)

which oddly enough describes how to create a script in the /etc/ppp/ip-up.d/ directory to create the required route.

so I did that and so far so good

hope it helps someone

---

