---
title: "How do I connect to the router connected to my router?"
date: 2008-05-15
forum: Networking &amp; Wireless
---

### Post by 50words on 2008-05-15
Here is how the network is set up:

```

Internet
|
Modem
|
Router1
|
Router2
|
My computers

```

I need to get to Router1 in order to forward a port. How do I find its internal IP address from my computer? How do I connect to it from my computer?

---

### Post by andrewc6l on 2008-05-15
From a command line on one of your computers, try:

```
traceroute www.bbc.co.uk
```

The second address line should be the IP address of router1, assuming it's pingable.

---

### Post by 50words on 2008-05-15
Okay, so that worked. But how do I get to that address in my browser? Both routers have the same internal IP address (192.168.0.1). If I use [http://192.168.0.1](http://192.168.0.1), I end up at my router, not the next one up the line.

---

### Post by eldragon on 2008-05-15
how confusing, im interested in the solution too.

id try switching one of the routers to another network, maybe 192.168.1.1

but then, those are non routable, maybe you need to set a manual route, but i do not know about how to set that up. and most definately, it has to be supported by the router.

---

### Post by Mr A Mouse on 2008-05-15
1. Take one of your computers and plug it into the first router (closest to the modem). Name it as router01 and set that router's IP address as 192.168.1.1, and turn DHCP off.
2. Unplug from the first router, plug into the second. Name it as router02 and set it to 192.168.1.2 (again, turn DHCP off).
3. Set your computers in the range of 192.168.1.10 - 192.168.1.254 (this leaves you a bit of slack space in case your network expands and you need to install more routers), and name them as appropriate.

In this case, you are using your routers as plain switches with no routing capabilities. You can either set your NAT settings on router01 (thus using it as a router again), or you can set up one computer as a gateway for the other computers.

---

### Post by 50words on 2008-05-15
There are actually three routers between the modem and my computers. Each has an IP of 192.168.0.1. I cannot change the other two, although I could change mine, if I knew how.

---

### Post by Mr A Mouse on 2008-05-15
> **50words said:**
> There are actually three routers after the modem. Each has an IP of 192.168.0.1. I cannot change the other two, although I could change mine, if I knew how.

Do you not have access to the other two routers?

You can change yours by opening a browser and typing "192.168.0.1" in the address bar.

---

### Post by 50words on 2008-05-15
> **Mr A Mouse said:**
> Do you not have access to the other two routers

I don't know how to access them, which is why I posted this thread!

---

### Post by Mr A Mouse on 2008-05-15
> **50words said:**
> I don't know how to access them, which is why I posted this thread!

Oh, I'm sorry for my confusion. That's why I was having you unplug a computer from your current router and go program the routers one by one.

---

### Post by 50words on 2008-05-16
> **Mr A Mouse said:**
> Oh, I'm sorry for my confusion. That's why I was having you unplug a computer from your current router and go program the routers one by one.

Now I understand. I don't know why I didn't think of something that obvious.

I still would like to know, though, if there is a way to get to each router through the network. Something like [http://192.168.0.1::192.168.0.1?](http://192.168.0.1::192.168.0.1?)

---

### Post by Mr A Mouse on 2008-05-16
> **50words said:**
> Now I understand. I don't know why I didn't think of something that obvious.

I still would like to know, though, if there is a way to get to each router through the network. Something like [http://192.168.0.1::192.168.0.1?](http://192.168.0.1::192.168.0.1?)

Not that I can think of while they all have the same IP address.

---

