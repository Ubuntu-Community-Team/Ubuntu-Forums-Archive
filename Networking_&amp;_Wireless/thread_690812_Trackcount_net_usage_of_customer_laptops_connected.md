---
title: "Track/count net usage of customer laptops connected to internet via Squid proxy?"
date: 2008-02-07
forum: Networking &amp; Wireless
---

### Post by kathryn on 2008-02-07
I've done my best to ensure this question hasn't been asked before on this forum (read many threads) and googled first to check if the solution is easy/obvious.  I'm new to this kind of stuff (proxies etc).

My dad knows someone who runs a Bed & Breakfast, and they want to offer internet access (via network cable, not wireless) to customers who bring laptops.  However the owner is smart enough not to unleash the customers onto the broadband account without first tracking their usage, since the B&B can host up to 5 separate couples/rooms at once.  If the owner can track their internet usage (i.e. only in terms of the quantity of data, not the sites they visit) then she can bill them accordingly.

Cost is a key factor, which led me to wonder whether she could use a Linux computer as a proxy (e.g. with Squid) between her ISP access and the laptops.  I understand that Squid generates a log file, and that there are programs to help a non-technical user 'analyse' the usage per computer connected.

The ultimate question (initially) is whether she can track _any_ computer that connects, without having to modify anything on the customers' laptops?  Obviously it would be intrusive and impractical to modify the internet settings and/or install tracking software on every machine that is brought through the B&B.

Any ideas?

---

### Post by sqrt2 on 2008-02-08
If you wnat to redirect all traffic to a web proxy, you will have to block all the other traffic at the router (which can be the same Linux box as the proxy), because it's trivial to bypass such a proxy by simply tunneling everything over a different protocol. (This protocol can even be HTTPS.) Since you have to filter traffic anyway, you can basically just run squid in transparent mode, e.g.

[indent]http_port 3128 transparent[/indent]

in squid.conf, and redirect all HTTP traffic to the proxy using DNAT, like

[indent]iptables -t nat -A PREROUTING -p tcp -m tcp --dport 80 -j DNAT --to-destination 127.0.0.1:3128[/indent]

---

