---
title: "Routing help"
date: 2008-04-08
forum: Networking &amp; Wireless
---

### Post by chadeldridge on 2008-04-08
Hello all, I need a bit of help with routing.  I have tryed a few configs and I cannot get something very basic to work.  I am using firestarter fyi.

I have 2 network cards in this machine (1 Internet "cable modem" and 1 internal network)

I want to have network card eth0 (internal network) handle all traffic for packets bound and from my internal network and eth1 (cable modem) for all connections to the internet. 

For some reason it seems that though all traffic, including my connection to the exchange server is attempting to go across the cable modem.  Can anyone help me with the router please?

Internal network  a.b.c.x/24
External network DHCP from cable modem 
The internal network also has about 5 other networks under it for our different sites around the world.  Would i have to setup a static route for each of those sites as well forcing them to use eth0?

Thanks

---

### Post by The Cog on 2008-04-08
Your eth0 should have an IP address and subnet mask that provides you with a route to devices on that cable. You should be able to ping those devices now. 

For every other internal network number, you will need to configure a specific route and a default gateway (the IP address of your local router). 

The command **route -n** will show you your current routing table. To add routes to the other internal networks, the command is
```
route add -net a.b.d.0/24 gw a.b.c.x
```
where a.b.d.0 is the internal network and a.b.c.x is your local router.

It may be worth disabling the firewall until you're happy the routing works.

---

