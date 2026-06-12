---
title: "Ubuntu router/webserver on ADSL to do pptp?"
date: 2007-04-19
forum: Networking &amp; Wireless
---

### Post by adjman on 2007-04-19
This may well be one of those things that isn't possible, but you don't know if you don't ask.

I have an Ubuntu Edgy machine set up as a Firewall/Router/WebServer on a Zen internet ADSL link. The ADSL connects using a speedtouch modem and then eth0 (3com network card) shares this out to the clients using iptables.

I have installed pptp on the Ubuntu machine and got it to the stage where it is working, in that a client can dial up and connect to the VPN using a given username and password - the problem then is that the newly connected client cannot do anything. It cannot ping itself, it cannot ping the ppp1 interface of the VPN it cannot ping anything on the internal network it should now be part of.

So, I am thinking that I have got something wrong in either pptpd.conf or the pptpd-options files?

The other thing is as the VPN connection is coming in on ppp0 (the speedtouch modem) and creates a new interface ppp1 this may be causing conflicts.

It might also be the iptables rules not forwarding stuff properly?

Any ideas would be great, cheers folks!

---

### Post by GTvulse on 2007-04-20
You have a problem with internal routing and bridging. I suggest you have a look at the [Linux Advanced Routing and Traffic Control How-To]("http://lartc.org/"). The connection your want to use for bridging is ppp1

---

### Post by adjman on 2007-04-22
Hmm, had a look through the documentation, but it's not written in the usual easy-to-understand Ubuntu speak - it's written in Advanced Router speak and I am not exactly sure what to do to get routing from the PPP1 interface that pptpd sets up and the PPP0 interface which is my internet on the ADSL Speedtouch modem.

I have tried getting ProxyARP to work, but no joy there and had a tinker with the routing tables, but the last thing I want to do is set up the routing tables incorrectly and then kill me current internet connection - I guess what I am doing is advanced stuff and there is no easy answer to the problem.

Had a look at openvpn as well, but when I implemented this using a how-to it killed my broadband connection, so I guess there is a severe lack of knowledge here that I don't have the capacity to fill in :( hey ho...

---

