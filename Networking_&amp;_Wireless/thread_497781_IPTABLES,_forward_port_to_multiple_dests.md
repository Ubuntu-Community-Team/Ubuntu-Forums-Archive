---
title: "IPTABLES, forward port to multiple dests"
date: 2007-07-10
forum: Networking &amp; Wireless
---

### Post by SundaY82 on 2007-07-10
Hi,

I have several computers on my network that require port 113 for ident, even the ubuntu server I use for sharing/routing my internet conneciton. So I would like to know if there is a way to forward a packet to 
multiple destinations (including the router box itself) using iptables?

Can this be done, either by some copy function or by some magic workaround?

Would really appreciate it if someone has a solution for me.

Thanks!

---

### Post by kidders on 2007-07-11
Hi there,

I may be misunderstanding your post, but the concept of forwarding the same port to more than one place doesn't make sense. If you think about it, you will see that an unsolicited incoming packet can't be destined for more than one location.

---

### Post by SundaY82 on 2007-07-11
your right, a specified package is only ment for one destination but i have several boxes on the network who all need to be able to respond to ident requests, so isnt it possible to just send the package to all boxes and then the one that feels to respond to that specified package at the time can return a message. I dont know if that mad it any clearer. Or how do peaple solve it when they have several boxes on the same line who need to use the same port?

---

### Post by kidders on 2007-07-11
Hey again,

I'm afraid what you're describing is not a good idea. Armed with an in-depth knowledge of network communications, you *might* (theoretically) be able to invent some sort of workable hack, but it would require so much work that it would hardly be worth it. Essentially, what you're asking (I think) is this:

Imagine a DSL modem with two PCs connected to it, both of which are running Apache servers on port 80. A HTTP GET request arrives at the modem, which is somehow manipulated into replicating the request and delivering it to two PCs (neither of which it was even originally addressed to). Even if that much could be made to work, you'd still have to find some way of forcing one of the PCs to selectively violate TCP protocol specifications.

In practice, *something* must exist to allow a router to distinguish between two packets. Source/destination IPs & port numbers are normally used (although there is a small number of other, more obscure possibilities), so you simply can't bind more than one server to the same IP/port combination. Your options are:[LIST=1]
[*]Vary the port numbers: If you were running two mail servers off the same IP address, for example, one could bind to port 25 (as normal), and the other could use an unreserved port (eg 10025).
[*]Vary the IP addresses: A network device can have more than one IP. Depending on how advanced your router is -- iptables will certainly have no trouble -- you could use the destination IP to differentiate between packets for NAT purposes.[/LIST]Your local situation may be different, but in Ireland, commercial ISPs are legally *required* to offer extra IPs free of charge (subject to regulator approval); conversely, domestic ISPs are forbidden from doing so. So, depending on your circumstances, option #1 may be the only one open to you. :-( As you are no doubt acutely aware, running services on non-standard ports can create problems. For example, MacOS is not easily manipulated into looking for Windows shares on ports other than 139. In some cases though, there are application-specific solutions available. Returning to my mail server example, for instance, several companies offer cheap (or even free) relaying services, allowing you to transparently run mail servers on the "wrong" port.

I'm sorry I can't be more encouraging.

---

### Post by SundaY82 on 2007-07-11
Thanks for your informative answer.

I can only get one public ip so that option is out, and the service its about in this case is ident, ie port 113 and that cant be changed for my applications. So i guess im all out of luck in this case :(

---

### Post by Synflux on 2007-07-12
Could you forward the port to the broadcast address for your subnet?

In theory it would send the ident request to every host on the network? How they would then respond I have no idea.

Would it work? I haven't a clue. just a thought.:confused:

---

