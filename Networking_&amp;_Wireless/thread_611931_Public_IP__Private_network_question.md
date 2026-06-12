---
title: "Public IP / Private network question"
date: 2007-11-13
forum: Networking &amp; Wireless
---

### Post by chrols on 2007-11-13
I'm currently getting my internet connection through a ethernet wallsocket. I get a public IP by DHCP from it. 

Now I've gotten an additional computer and would like to have it connected to the net as well, since I only have one IP my first computer would have to have masquerade set up. I've done this before with other machines so I'm a bit familiar with it.

The diffrence here is that no computer have two ethernet cards.

So my main question is: Would it it be possible to connect the wallsocket to an ethernet hub as well as the other two computers and having one getting the DHCP IP and then masquerading allowing the other computer to connect to the internet through it?

Connecting just the first computer and the wallsocket to the hub everything works just as if I had connected the wallsocket cable directly into the first computer

Connecting the second one had been tricky, it's an old computer with rather obscure hardware as well. I've gotten the both computers to see eachother when I unplug the wallsocket cable and set them up to 192.168.1.1 and 192.168.1.2.

I've tried for quite a while to get it working though I keep having this thought that what I'm hoping to set up can't be, I would need a card for the wallsocket and then one for the internal network. 

If it is possible, how would one go about setting it up?

---

### Post by jetsam on 2007-11-13
I don't think you can do this with just a hub.  You'll either need a second ethernet card in one of the machines to set it up as a gateway for the other machine, or a hardware router which can do connection sharing.  
Home routers aren't very expensive and using one with a firewall built in has some security advantages over connecting directly into the network, so that's the way I would go...

---

