---
title: "two different networks on one Linux box."
date: 2008-02-06
forum: Networking &amp; Wireless
---

### Post by sven86 on 2008-02-06
Hi, I have in my home two separate networks, each controlled by a router and they are connected to the internet. I also have a Ubuntu machine which happens to be a media/file server.  I would like for the machine to be able to connect to both networks so that the computers on both networks can access the server, what is the best way to go about doing this?  My server does have two network cards.
  
I read about OpenVPN, route, iptables, bridges and other things but they're very confusing to me.

---

### Post by PaulFr on 2008-02-06
IMHO, the simplest solution for you would be to assign one static IP address from the first network to one card of your server, and one static IP address from the second network to the other card of your server.

This assumes that:

a, the two networks have (*or you can configure them to have*) different non-overlapping range of IP addresses (for example, one could be 192.168.0.1-255 and the other could be 192.168.1.1-255).

b. you do not need to access any other resources on either network through this server - when you do need to, read up about setting up IP forwarding.

---

### Post by sven86 on 2008-02-06
> **PaulFr said:**
> IMHO, the simplest solution for you would be to assign one static IP address from the first network to one card of your server, and one static IP address from the second network to the other card of your server.

This assumes that:

a, the two networks have (*or you can configure them to have*) different non-overlapping range of IP addresses (for example, one could be 192.168.0.1-255 and the other could be 192.168.1.1-255).

My server already has one of the cards assigned a static IP address via the D-Link router.  As for the other card it will be connecting to a Belkin Pre-N router through wireless but the router doesn't provide static IP addresses AFAIK.  I'll have to do it on Ubuntu's side.

Both networks have different IP ranges (one 192.168.0.x and the other 192.168.1.x) so that's not a problem.

> b. you do not need to access any other resources on either network through this server - when you do need to, read up about setting up IP forwarding.

I'm assuming you mean accessing other computers on the opposite network.  You're correct on that one but who knows in the future.  I might as well read up on it after I get it set up.

---

