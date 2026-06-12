---
title: "network within a network?"
date: 2010-11-04
forum: New to Ubuntu
---

### Post by jonnny_j22 on 2010-11-04
Hi all,
 
little bit of background, we live in a shared house that we have divided into three private residences. To save money on our internet bills, we get a communal 50meg internet from our cable provider and use a router to provide a wireless network throughout the building and also send an ethernet cable to each apartment. 
 
In our apartment we have a desktop pc, two laptops, an Iphone, a Blackberry and a PS3 that all connect to the internet. Our desktop is new and I was thinking we could use our old one as server as it's pretty well suited to this (low power consumption mac mini) so we could access all our data easily from our various devices. 
 
Is it possible to set up a network within a network? (we don't want to share EVERYTHING with our neighbours!) Bascially I'd like to use the old mac as a server running ubuntu, and connect through the ethernet cable that comes to our apartment (from a router connected directly to our cable modem)
 
would I have to have two ethernet adapters on the mini mac, or could I use a second router?
 
Any help you can offer would be greatly apreciated!

---

### Post by sandyd on 2010-11-04
> **jonnny_j22 said:**
> Hi all,
 
little bit of background, we live in a shared house that we have divided into three private residences. To save money on our internet bills, we get a communal 50meg internet from our cable provider and use a router to provide a wireless network throughout the building and also send an ethernet cable to each apartment. 
 
In our apartment we have a desktop pc, two laptops, an Iphone, a Blackberry and a PS3 that all connect to the internet. Our desktop is new and I was thinking we could use our old one as server as it's pretty well suited to this (low power consumption mac mini) so we could access all our data easily from our various devices. 
 
Is it possible to set up a network within a network? (we don't want to share EVERYTHING with our neighbours!) Bascially I'd like to use the old mac as a server running ubuntu, and connect through the ethernet cable that comes to our apartment (from a router connected directly to our cable modem)
 
would I have to have two ethernet adapters on the mini mac, or could I use a second router?
 
Any help you can offer would be greatly apreciated!
easy.
just get a router/switch (router reccomended so that you can use dhcp)
get a extra ethernet card for the mac (has to be mac compatible, there are some mac incompatible cards out there)

setup squid proxy server.

set the proxy on all computers to the ip address of the mac

---

### Post by holiday on 2010-11-04
One ham-fisted solution would be to give all your devices static IPs and have each one firewall everything else out. 

I'm not sure that all devices offer that granularity.

Just a thought. Hopefully there's a better solution.

What if you put a router on your local wired feed? Maybe that would work. I think it might.

---

### Post by Gone fishing on 2010-11-04
There are many ways.
You could use the old PC as a gateway server one NIC to connect to the net and one NIC to connect to you internal network. The sever could then use IP forwarding or even squid to share the internet many distros would do that perfectly. Pfsense with IP forwarding would work very nicely for just sharing the internet.

If you want the sever to do more it could also act as a file sever with samba.

---

### Post by jroa on 2010-11-04
As stated earlier, there are lots of ways to do this.  One easy way is to just password protect your shared folders.  Only the people in your apartment who know the password would have access.

A router would be a better solution, in my opinion.  You can easily set up your private network, plus the router will probably offer extra firewall protection as well.  A wireless router would also let you have access to your portable devices.  This is the best option to me.

A switch could work, but for me, configuring a router is much easier than a switch and the router has many more feature than a switch too.

Subneting might be an option, but that would involve the entire network.  Someone would have to plan this and implement it throughout the network.

---

