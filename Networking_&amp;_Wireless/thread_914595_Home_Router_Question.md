---
title: "Home Router Question"
date: 2008-09-09
forum: Networking &amp; Wireless
---

### Post by TreeFinger on 2008-09-09
I have a question about the hardware for a Home Router.

I understand the setup will be Modem > Linux Router > Switch => Computers in network.

My question comes down to the cables I will need.

I am wondering where I will need straight through cable and where I will need cross over cable.

Will I need straight through cable between the modem, router, and switch?

Or just between the Modem and Router?

Also, to use my current router as just a switch, I just need to turn off DHCP on the router, correct?

---

### Post by TreeFinger on 2008-09-09
bump

---

### Post by jimv on 2008-09-10
You shouldn't need crossover cables anywhere.

And yes, turning off DHCP will make the router essentially a switch.

---

### Post by TreeFinger on 2008-09-11
Well, If I am plugging the home made router into the uplink port, won't I need crossover cable there?

---

### Post by bab1 on 2008-09-11
> the setup will be Modem > Linux Router > Switch => Computers in network.

The connection from the Modem to the Linux router is really from modem to nic and no x-over cable is needed.  Any connection between  the nic and a switch needs no x-over cables.  I don't see any need to have x-over cables in this situation.  
> Also, to use my current router as just a switch, I just need to turn off DHCP on the router, correct?

A switch **replicates data input on a port to all other ports**.  By definition a multi-homed linux host (router) is not switch.  DHCP has nothing to do with it.

---

### Post by Iowan on 2008-09-12
> **bab1 said:**
> A switch **replicates data input on a port to all other ports**.Switch or hub?  I thought switches "learned" to replicate data only to the port with "target" address (MAC?). Dunno, I'm asking...

---

### Post by bab1 on 2008-09-12
The switch does not learn to replicate.  Its built in to the chipset.  The data is replicated to all the ports.  The fact that these are **separate** is what keeps the collision domains separate.  In a hub all the ports are on a common wire.

---

### Post by timcredible on 2008-09-12
> **bab1 said:**
> 
A switch **replicates data input on a port to all other ports**.  

no.  a hub sends all packets out all ports, a switch only sends unicast packets out on the port that it's destined for.  both hubs and switches send all broadcast packets out all ports.  multicast is kind of in between the two.

---

### Post by bab1 on 2008-09-12
@timcredible

Your right!  I stand corrected.  :-(

---

