---
title: "Sharing a printer on multiple subnets"
date: 2008-10-28
forum: Networking &amp; Wireless
---

### Post by JeppeM on 2008-10-28
Hey all,

In your office we have several different companies. We (myself and a coleague) are in charge of the network, and we currently have a big printer connected to the 192.168.6.xxx network, I don't know exactly how, since we just took over the network admin role, all i know is that the server is running linux (red hat i think, but i'm considering moving to ubuntu). But, the other companies at the location use 192.168.22.xxx, .50.xxx, .129.xx etc, and some of them want access to the printer.

Is there any good way of doing this? One possible solution would be to plug in 5 NICs in the print server, but i don't think that that solution is the best, seeing that we might get more than 15 subnets at one point...

Anyone here have any ideas about this? Sorry if my explanation isn't the best, as i said, network administration isn't my strongest side ;)

---

### Post by Iowan on 2008-10-28
All those networks share a common wire, or is there a router in there somewhere?

---

### Post by JeppeM on 2008-10-29
The all have their own gateways which are connected to a switch, which is connected to our outgoing lines... We currently have three different outgoing lines, which they're connected to (one outgoing line for .6 and .22, another for .50 and .129). Thanks a lot for your help Iowan

---

### Post by JeppeM on 2008-10-31
No one have any idea about this? :(

---

### Post by superprash2003 on 2008-10-31
well if you are running linux, you could try forwarding all traffic from those gateways to a totally different server machine which has the printer attached , that way it should be recognized on the network.. connect it to a common switch.. a switch with the print server( which is a pc with printer) and all other gateways.. you would need multiple NICS on the gateway though..

---

### Post by JeppeM on 2008-10-31
Thanks superprash,

I guess that would require at least three NICs in the gateways ,right? One for the outgoing line, one for the internal line, and one for the switch which the print server is connected to?

I guess thats doable, without too much fuss :)

---

### Post by superprash2003 on 2008-11-01
right..

---

