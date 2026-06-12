---
title: "No access to my server via Vodafone UMTS modem"
date: 2008-11-22
forum: Networking &amp; Wireless
---

### Post by The Foz on 2008-11-22
I do understand that this is not actually a Linux problem, but I was hoping that someone might be able to shed some light on this problem.

I recently bought a Vodafone (actually a Huawei E220) USB UMTS modem.

After some teething troubles, I got it to connect to the Internet, and set up Internet Connection Sharing on my server. Internally, everything now works fine. I have access from all machines connected to my LAN, via the server, to the Internet, using the Vodafone Germany UMTS service. The bandwidth is excellent.

What I cannot do is connect to my server from the Internet. All traffic initiated from the Internet (e.g. from my office) is blocked, including ping traffic. This is a great nuisance, as the server is a web-server & email server.

It would seem that Vodafone has a firewall on their UMTS access points that blocks traffic initiated from the Internet. I am sure they feel that this "adds value"; I don't see it the same way.

Has anyone experienced the same problem? Does anyone know of a work-around?

---

### Post by SpaceTeddy on 2008-11-22
i don't the problem (wish i would, but cannot afford it), but i do know a workaround... you need to relay your traffic. But if you do that, you might aswell move your entire server to the relay, as it will not not work without. 

The reason this works is because the server will initate a connection to a third a party on the internet and keep this open. Since firewalls will only block incoming and not outgoing connection, this will be possible. But what data flows within the connection (i.e. from or to the server) is not visible to the firewall (especially when you encrypt it) - so what you do is connect to the third party and use the backchannel of the already existing connection to get to your server. 

AS i said, this is a relay - and makeing the relay your server is probably easier than having the relay.. but it is the only way i can think of (at the moment)... 

what do port scans say when you scan yourself from the internet ? is there anything open or is all stealthed/rejected ?

---

### Post by The Foz on 2008-11-22
I am not able to do a port-scan from outside, at the moment. The only remote system that I can use from at home is the office (via VPN), and the security there stops me installing or running port-scans.

Running a port-scan from the server, on the Internet (ppp0/UMTS) interface, shows that all the expected ports are open (HTTP, SMTP, IMAP, IMAPS, POP, POPS, SIEVE, LDAP & LDAPS), but of course the scanning traffic is never actually leaving the server.

I have actually tried access to pretty much all the services on the various ports (from the office), and they are all blocked (not reachable). I have checked that they are not being blocked by my firewall, but there are no events being registered from the Internet, and no active connections from the Internet except those initiated by the server.

Regarding cost, I was actually surprised at how cheap it was. It is costing €35 per month, which is comparable with DSL prices. It is a flat-rate tariff. The first 6 months are free (no monthly charge), which gives an effective monthly cost of €26. The UMTS USB modem was included (€1 down-payment, and a 2 year contract commitment).

---

### Post by Neostar on 2008-11-22
Well Vodafone do support Linux so have a look at there website, they also have a forum for help on these things.

[http://www.betavine.net/bvportal/web/guest/projects](http://www.betavine.net/bvportal/web/guest/projects)

---

### Post by SpaceTeddy on 2008-11-22
search google for "shields up" (grc.com or something like it) - they do portscans of the ip-address that is connecting to their website... you don't need any external system for that.

---

### Post by The Foz on 2008-11-25
Hi NeoStar,

I think you have misunderstood my problem. I have all the software that I need (included in Ubuntu 8.04). A new driver is not going to help.

I now have more information. It is not a firewall issue. There is simply no route to my server (attached via the UMTS modem). I have tried doing TraceRoute, by several different methods, from different clients; it always finds a few way-points and then fails to find a route.

This is the reason why ping, port-scan, and trying to access my web-site all fail.

There are, of course, outbound routes. I can access sites and services on the internet from my home LAN. There are simply no inbound routes.

Is there any way that I can force a route to be created for inbound traffic?

---

### Post by SpaceTeddy on 2008-11-25
this would mean that you are behind some nat or something like that... if you have no inbound rules. 

Are you sure that you have no route, or that simply inbound connection are being blocked ? But then, i would not know how to find out the difference... not much you can do about it other than ask your provider to allow inbount connection...
the only other thing is that you got to use a relay... but we've been over this before.

sorry :(

---

### Post by The Foz on 2008-11-25
As far as I know, TraceRoute should find routes, if any exist, even if traffic is blocked (e.g. by a firewall). Unless of course the routing protocols themselves are blocked by Vodafone, which seems unlikely.

The odd thing is that occasionally (maybe 3 or 4 times a day) I see traffic from within the Vodafone network blocked by my firewall (never from anywhere else). Maybe it is all a problem with my router set-up on the server; perhaps I have the routing protocols blocked (I will check that tonight).

---

### Post by SpaceTeddy on 2008-11-25
the routing procolls that vodaphone uses internaly doesn't matter to you - they are just for making sure that that their internal routes are set correctly. That is vodaphones task and should be transparent to you !

What you are doing with a traceroute is send icmp messages. If they get blocked or dropped somewhere, it will look like a blackhole or missing route, but it will acctually just be a firewall/packet filter that is handling the icmp packets wrong. 

I don't think you need any routing protocol on your server to handle this kind of setup...

---

### Post by The Foz on 2008-11-25
...

---

### Post by Neostar on 2008-11-25
In that case can I suggest you switch to the 3 network.

---

