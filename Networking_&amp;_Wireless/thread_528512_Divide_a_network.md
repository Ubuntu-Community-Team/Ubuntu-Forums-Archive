---
title: "Divide a network"
date: 2007-08-18
forum: Networking &amp; Wireless
---

### Post by jrd on 2007-08-18
I am installing 8 computers on an existing network of about 15 computers. I need the 15 computers to be invisible to the 8. They all need internet though. Right now the set up is the 8 computers go through a switch then to a router. The same router is the default gateway to the whole network. Thanks in advance for the help.

---

### Post by jrd on 2007-08-18
anybody???

---

### Post by Synflux on 2007-08-18
Um, depends on the model of router I guess. Basically you need to put them in two different subnets but most consumer grade routers only allow one lan side IP address.

E.G.
Existing computers could use 192.168.0.0/255.255.255.128 and
new computers could use 192.168.0.128/255.255.255.128 

With a firewall you allow access only to the local subnet but the router would need an ip address in each subnet.

---

### Post by callan79 on 2007-08-18
> **jrd said:**
> I am installing 8 computers on an existing network of about 15 computers. I need the 15 computers to be invisible to the 8. They all need internet though. Right now the set up is the 8 computers go through a switch then to a router. The same router is the default gateway to the whole network. Thanks in advance for the help.

Hello jrd,

I've done this several times for my customers at work, where the customer has two networks that share one connection.

This is kind of hard to explain .... but basically you get one ADSL Gateway Router (example, Linksys AG241, Billion 7402, etc) and you disable NAT (network address translation). You ask your Internet provider to give you multiple Static IP addresses. You'll need 1 IP Address on the Router WAN, and three on the Router LAN (note - the actual router lan takes one, then you need two more).

Then into the Gateway Router, you plug a normal Ethernet Router (example - Linksys WRT54G), and you do Internet sharing to the networks.

The networks are then separate, but share a common gateway!

If this makes no sense please ask, and I can draw a diagram for you.

Regards,
Callan

---

