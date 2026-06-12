---
title: "Proxy server questions"
date: 2007-10-11
forum: Networking &amp; Wireless
---

### Post by evolvedlight on 2007-10-11
Hey

I'd like to use an ubuntu server as a sort of proxy and I just want to check out with some people here that it would work as I want it to.

Basically, I'm connected to a network (uni network) and they don't want hubs directly connected to their access points. So, I was thinking of having a computer with two Ethernet cards (ubuntu computer), with one plugged into access point and one plugged into router/switch.

The uni network cannot be allowed to detect that any of this is happening - it should just look like a single computer plugged into the network. 

What I have been doing is logging into big computer via NX/VNC and using internet that way. Is it possible to use a HTTP Proxy / other type of proxy to do a similar effect, but without having to mess around with VNC and the like

What I want to be able to do is connect the the network, set a http proxy, and use internet like normal. However, if this means that my internet traffic looks different then it's out of the question.

Is this possible? Would it work? 

Thanks

Steve

---

### Post by spd106 on 2007-10-15
It sounds like what the Uni doesn't want is lots of individual computers with their own IPs. This is understandable on a large network, but what you can do is set up NAT to keep them happy by creating your own network with private addresses.

Most home routers are setup this way by default and as long as you have one with an Ethernet port rather than the combined ADSL modem, you should be ok. So it might be worth finding if you can have a router attached to the network as long as you use NAT.

If really want to use the PC as a pass-through then you can use Firestarter to share the connection and optionally use a web proxy such as Squid.

[https://help.ubuntu.com/community/InternetConnectionSharing](https://help.ubuntu.com/community/InternetConnectionSharing)
[http://www.squid-cache.org/](http://www.squid-cache.org/)

---

### Post by ma2d_te on 2007-10-17
ok... thanks a lot. That information I needed.

---

