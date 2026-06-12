---
title: "Can I Combine 2 Internet Connection?"
date: 2007-06-23
forum: Networking &amp; Wireless
---

### Post by kenweill on 2007-06-23
Can I combine 2 internet connection? Will it double the speed?
Example, 2 dial up modem connected to a single pc or to a network.

I have a computer, a gateway. I have 1 internet connection. A kind of dial-up connection. Wireless. Using a HUAWEI wireless modem. Im currently not satisfied with the bandwidth. It cannot be increased. Its powered by GPRS. 

I wondering, if I connect 2 HUAWEI wireless modem to my gateway, does it double the speed? I also want to know how is it done.

---

### Post by kidders on 2007-06-24
Hi there,

What do you mean by "combine"? A standard TCP socket, for instance, can obviously only be bound to one IP address, so I'm not too sure what you have in mind.

---

### Post by kenweill on 2007-06-25
Install it in one pc, the gateway. Is it possible to install 2 internet connection in 1 pc? Then share the connection to the workstations. Will it double the speed?

Example.
I have a device, 1 device that is able to connect to the internet with the maximum of 128kbps bandwidth.
I want to add another device, thats also can produce 128 kbps bandwidth.

If i connect both, the 2 device in one pc, will it work? Can it produce 256kbps bandwidth? This pc is a gateway, with 192.168.0.1 address.
If my workstations points to the gateway, will it have 256 kbps bandwidth?

---

### Post by netztier on 2007-06-25
> **kenweill said:**
> Install it in one pc, the gateway. Is it possible to install 2 internet connection in 1 pc? Then share the connection to the workstations. Will it double the speed?

Example.
I have a device, 1 device that is able to connect to the internet with the maximum of 128kbps bandwidth.
I want to add another device, thats also can produce 128 kbps bandwidth.

If i connect both, the 2 device in one pc, will it work? Can it produce 256kbps bandwidth? This pc is a gateway, with 192.168.0.1 address.
If my workstations points to the gateway, will it have 256 kbps bandwidth?

Simple Answer: no you can't.

less simple answer: If you are using PPP (for instance with ISDN or 56k Dialup) AND you dial to the same provider multiple times AND this provider supports **multilink PPP**...  then yes, it might work. But you need good knowledge of networking and PPP, and probably a good technical peer to talk to at the ISP you are using. Like this, you can increase the speed - usually at the **double of the dialup cost**, of course.

If you are talking about "multiple different ISPs": no, you can't increase speed for a single connection.

The problem is that the ISPs are going to give you different external IPs to use - and for a single connection, you can't have some packets use ISP A and  IP source address A, while some other packets of the same connection use ISP B and the IP address you got from ISP B.


However something like this might be feasible:

It may be possible to have one Ubuntu Router connected to two different ISPs. It does not matter which technology they use, just as long as the router can obtain an IP address from the provider; be that Dialup or ISDN iwth PPP, GRPS, UMTS with or without HSDPA, xDSL or cable, even some public WLAN.  But I think that for satisfactory results, both connections should have similar bandwiths.

You then need some **clever routing and NAT configuration** that knows how to make an individual connection "**stick**" to one of the external interfaces. This will not increase the speed of a single connection, but by distributing all connections to the (two, maybe more?) external interfaces, the total capacity increases. I cannot tell for sure if **iptables** can actually do this - but from a dark corner of my memory, I think I've read about it somewhere. If I find it again, I'll post it here.

*Edit: *
[LIST]
[*]*it seems that shorewall (which configures netfilter/iptables) can do this: [http://www.shorewall.net/MultiISP.html](http://www.shorewall.net/MultiISP.html) - but this is advanced stuff.*
[*] *no less advanced: [http://linux-ip.net/html/adv-multi-internet.html](http://linux-ip.net/html/adv-multi-internet.html)*
[/LIST]


best regards

Marc

---

### Post by kidders on 2007-06-25
Yep... I agree with netztier. The best you could hope for would be an *average* increase that would theoretically approximate the total available bandwidth, but only where the protocols you use are capable of spreading their activity over multiple simultaneous connections.

For instance, a web page can be (but isn't necessarily always) loaded over several simultaneously established HTTP connections between you and the remote host. What netztier has in mind might be the possibility of configuring a gateway (perhaps a HTTP proxy) to bind each of them randomly to different network interfaces. Specific to the case of HTTP though, it would be difficult to anticipate what impact sudden, unexplained changes in your apparent external IP address would have on services that like/need to know it. In any case, this approach feels very like load balancing to me, so I'm sure it can be done with _relative_ ease, assuming you have a thorough understanding of network communications protocols.

Naturally, not all protocols would benefit from such an arrangement in the way HTTP can, because of the simple fact that  a connection between any more (or less) than two points doesn't make sense. The best you could hope for would, as I mentioned, be an average increase. In those terms, applications that failed to establish more than one network connection, individual network connections that remained established for any more than about a second, or failed to use 100% of the bandwidth available to them, would cause the increase to tend towards the individual bandwidth of your slowest internet connection.

Another way of looking at your question is to think of your internet connections as though they were CPUs.[LIST]
[*]Multiprocessor machines are essentially capable of handling two distinct processes at the same time.
[*]You cannot share one process between more than one CPU.
[*]If you are only performing one process, and it is using 100% of the CPU controlling it, there is effectively no point in having a second processor at all.
[*]If you are performing more than one process, but are not using all of the available CPU time, there is very often *still* no point in having a second processor.[/LIST]You could however consider designating one of your internet connections an "RTSP" connection, and the other a "HTTP" connection. Neither RTSP nor HTTP would go any faster, but neither would impact the bandwidth available to the other either. Essentially, you would be guaranteeing your ability to surf the web freely, without causing streaming media to stutter or freeze ... but each would operate (in speed terms) as though it was the sole user of a single internet connection.

---

### Post by kenweill on 2007-06-26
Is there any device that can do that automatically?
Its just that I've seen an internet cafe doing that kind of connection.
Im amazed with their connection speed compared to other internet cafes in the town. Their connection is faster than the other. They have the same ISP.

When I asked the personnel in there, he said that they are using 2 device, to connect to the internet instead of 1. And it doubles the speed. Those device are not connected to the computer but its connected to some, SWITCH like device. Maybe its a router. Im not sure. Don't know what a router looks like. I have never seen one. According to the personnel, he said its connected to a WAN. Not sure why. And he doensn't know how its done. He said that only the owner knows how its done. Theres no gateway. One can use the internet on any PCs, without the other powering on. Maybe its a router. I don't know.

Thats why im asking here. Perhaps one knows how its done.
The device is wireless. Using GPRS/EDGE signal.

---

### Post by netztier on 2007-06-26
> **kenweill said:**
> Is there any device that can do that automatically?


Check out the RV042 from Linksys ([http://www.linksys.com](http://www.linksys.com)) or it larger brother, the RV082. 

They have a feature that can do something like this - but they have Ethernet interfaces as "WAN" ports - you'll need some ethernet-capable device to connect it to. There's other companies that sell devices with similar features.

best regards

Marc

---

### Post by kenweill on 2007-06-26
Ok. Thanx alot. I'll try it. 
Btw, its not WAN. But he said Dual-Wan.

Anyway, I'll try to research more on LinkSys. Thanx alot.

---

### Post by Chappy7777 on 2007-06-26
All I can say is good luck! A few years ago I talked w/my ISP. They agreed to allow me to log in with 2 modems at the same time for 2 weeks while I tried to get "Multilinking" working. Windows does support this. With Linux I suppose that it is theoretically possible, but very very unlikely.

You must have 2 of the exact same modems (or whatever you are using to connect to the net), or it won't work. I tried w/2 USR Sportster 56K modems (ISA not winmodems, this was before winmodems), and could not get it to work. And again, I had 2 identical modems, a cooperative ISP whose owner was a friend, so we worked on this together. I had 2 phone lines, another requirement.

I think you are better off putting your energy into something else, like getting a faster connection via cable or DSL.

---

### Post by Ocxic on 2007-06-27
yes it is possible, I've seen a tutorial on how to do exactly that, take 2 serapt intyenet connections and use both at the same time from the same computer....I'f a can ever find that tutorial I'll be sure to get it to you.

---

### Post by kenweill on 2007-06-28
> **Ocxic said:**
> yes it is possible, I've seen a tutorial on how to do exactly that, take 2 serapt intyenet connections and use both at the same time from the same computer....I'f a can ever find that tutorial I'll be sure to get it to you.

Thanx man. I look forward to that. I'll wait till you find it.

---

### Post by Ocxic on 2007-06-29
i would suggest that we double our efforts, it's apparently hard to find... I was googling last night could find it...

I would like to point out that having a setup like this won't really make your internet any faster, in general..
however if you use things simialar to bit-torrent, then you'll see an improvment...

---

### Post by n1ght28 on 2007-12-03
hey i have a similar query, i have two DSL connections with two different ISP's one's mine the other is my friends in the flat beside me, i am wondering if we can combine the two to improve our speeds when bit torrenting and the like,  one is wireless and the other wired, i have both  wireless and wired network cards, is this feasible  or even  beneficial.

---

### Post by khoshtip on 2007-12-24
Yes you can, but not with the PC it self 
what you need is a device that integrates 2 or more connections and makes a single connection out of them.
as far as I know there is only one device capable of doing that and it is called Maha X-Sum Integrator witch I am using my self and works Grate with my 3 High Speeds witch are from 3 different ISP's 
(Comcast Cable, AT&T DSL, Surewest Fiber Optic )
as far as if it dos work with dial ups or not I don't know but you can Call Maha PC and ask them 
hair number is 888 - 462 - 0476 
hope it works out for you

---

