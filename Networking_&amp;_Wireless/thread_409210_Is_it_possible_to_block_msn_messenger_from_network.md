---
title: "Is it possible to block msn messenger from network?"
date: 2007-04-14
forum: Networking &amp; Wireless
---

### Post by tictacman on 2007-04-14
After spending fruitless hours trying to block msn on a home router the little critter still fires up :). Would be grateful if some one could tell me whether its even possible, or do I need to build some kind ubuntu powered gateway.

---

### Post by kidders on 2007-04-15
Hi there,

If a Linux box is routing your internet connection, blocking things is trivial, provided you can adequately describe the traffic you want to disallow. For instance, a quick web search suggests that the following would be a good description of MSN messenger data...[LIST]
[*]Outgoing on port 1863, or
[*]Destined for 207.46.110.0/25, or
[*]Destined for 207.46.104.20.[/LIST]Ubuntu can handle these sorts of basic restrictions, more or less out of the box (ie an **apt-get install** might be required to get you started). If you're not using Linux to route data on your network, whether you can successfully block MSN messenger traffic depends on how smart whatever you *are* using is, I suppose.

MSN is a complicated enough example, since it's (a) designed to use UPnP to reconfigure networks to allow its traffic, (b) quite tolerant of port unavailability, and (c) happy to use proxies. On top of that, there are many web-based interfaces to the MSN messenger service. Being sure you have all the bases covered is not the easiest thing in the world, unless something reasonably smart (like a Linux box) is managing your network.

---

### Post by tictacman on 2007-04-15
thanks very much for the reply.  Yes I have tried googling first, blocked port 1863 and just about every other port associated with messenger with the exception of 443 which would just be plain silly. Did me no good.  Also banned gateway.messenger.hotmail.com, blocked access to address 64.4.13.170 through to 64.4.13.190.  Didn't help one bit.

> # Destined for 207.46.110.0/25, or
# Destined for 207.46.104.20.

I didn't come across that bit of info before (so much for my searching skills) so I will give it a go. As for web messengers, I've done some research there and  have built a big fat list.  I never for one minute released just how pervasive messenger is, its like some pesticide defying weed has taken over my garden and the thing refuses to do die.  

Like you said if I probably need some kind of proxy server to defeat this menace.  Actually I wouldn't mind building something like this just for 'fun', and I've got a unused mobo+chip up in the attic.  This is only a tiny network probably 6 or 7 connections at most, anyone know what kind of minimum spec I could run something like this without X? Trouble is I would have get rid of my existing router modem and buy modem, a hub and a wireless access point which works out kind of expensive.

---

### Post by kidders on 2007-04-15
Hey again,

You seem to have spent quite a bit of time on this issue! Your lack of success is not encouraging :-( ... perhaps it's time to recruit a packet sniffer? You could, for instance, install Ethereal (also called Wireshark), start it listening, and log into MSN yourself. Ethereal is very nicely presented (comparatively speaking!), and displays a great deal of information about packet contents, some of which is *bound* to help you refine your firewall rules.

> **tictacman said:**
> As for web messengers, I've done some research there and  have built a big fat list.  I never for one minute released just how pervasive messenger is, its like some pesticide defying weed has taken over my garden and the thing refuses to do die.Lol that's possibly the best description of MSN I've seen!

> **tictacman said:**
> I probably need some kind of proxy server to defeat this menace.Yes... requiring the use of a proxy to gain internet access (or perhaps just proxying transparently) would certainly be a clean way of solving the issue of web-based interfaces to MSN in a single stroke.

> **tictacman said:**
> anyone know what kind of minimum spec I could run something like this without X?You might be surprised how low you can go ... although Ubuntu may not be the best choice of distro. Linux per se will run on extraordinarily low-spec devices (100s of MHz, with <100MB RAM, and very little storage space), which is one of the reasons 2.2 and 2.4 kernels are still maintained.

One option worth considering might be just to buy a cheap, dumb modem and a second network card (something for about &#8364;15, maybe). Depending on exactly what you've already got, and what your requirements are, you could maybe...[LIST]
[*]Pair up the cheap modem & NIC and plug them into a Linux box, which you would use as a router & proxy/DNS/DHCP server.
[*]On the local side of the Linux box, you could use your current modem/router (which I'm assuming has a wireless interface too) as a hub/switch/AP for your network.
[*]You could switch off the modem, DNS & DHCP servers, and other advanced features in the modem/router box, and give the Linux box full control of your network.[/LIST]If you want to go the proxy route to curtail web-based access to certain things, you could then install some filtration software (DansGuardian, for instance) to start blocking content. There are plenty of smarter content filters available too, which would help reduce the need for you to go trawling the web for hosts you should blacklist.

Without wanting to pry, I'm curious about your reasons for wanting to block access to MSN. Essentially, I'm wondering if the protection of children is the issue, and if so, whether they are your own. It's possible, for instance, that a combination of basic preventive measures and network usage logging (ie big brother!) would be a good solution for you ... but then again, you could have legal reasons for *needing* to comprehensively defeat any attempt to get access to MSN chat services.

---

### Post by tictacman on 2007-04-15
> Pair up the cheap modem & NIC and plug them into a Linux box, which you would use as a router & proxy/DNS/DHCP server.

Yes that sounds like the most sensible thing to do.  Not too many stand alone modems about but I found a few. I have a spare nik, spare hard drive, and the cpu is 1.8ghz, no memory but I would  probably get 250mb or 500 depends on difference in price. 

> Without wanting to pry, I'm curious about your reasons for wanting to block access to MSN

Let just say that we've had a guest to stay who hooked up to the network, and I was looking for a way to curtail the usage a bit (this is not really an issue any more since they are leaving).  Since then its become a bit of an obsession.  I think this could turn out to be a nice little project for me though, and might gain a little extra protection for the network.

---

### Post by kidders on 2007-04-16
Ahhh... I see. Well, blocking MSN won't really protect your *network* from anything in particular, but that doesn't mean you shouldn't be able to, if you want to.

The best way to exercise full, flexible control over what your internet connection gets used for is with a Linux box, imo. A 1.8GHz machine would be more than capable of handling that without breaking a sweat ... so would one half that speed though.

---

### Post by tictacman on 2007-04-17
Actually the 'protection' I was referring to was the 'added bonus' that would come with a linux server and firewall. I'm hoping to pick some knowledge up on iptables and security in general along the way.

---

### Post by kidders on 2007-04-17
Whoops! Do post back if you run into any trouble ... security is certainly something people will always be happy to help with. :-)

---

