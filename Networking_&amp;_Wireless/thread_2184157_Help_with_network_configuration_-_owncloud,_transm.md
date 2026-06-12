---
title: "Help with network configuration - owncloud, transmission, zoneminder all via HTTPS"
date: 2013-10-27
forum: Networking &amp; Wireless
---

### Post by fraser_john on 2013-10-27
Have been running a server for quite a while, including the firewall to avoid hackers and the like, but, in building a new server with ZFS and RAIDZ2 I want to drop the firewall management part and leave that up to an off the shelf router with just 80, 8080 and some port for transmission being left open. Opening the port via a router is a no brainer.

My problem is that I am not familiar enough with everything to confidently figure out and build the rules to do the next part. I want to run DDNS through afraid.org and have access to transmission, opencloud and zoneminder via HTTPS only. So if I access [http://mysite.chickenkiller.com/opencloud](http://mysite.chickenkiller.com/opencloud) I want to to force me to [https://mysite.chickenkiller.com/opencloud](https://mysite.chickenkiller.com/opencloud), once again, configuring a DDNS is simple and I have that for the current version of my server, but will be moving from dyndns.org (sick of the regular renewal crap).

The attached image shows my desired network configuration.
[ATTACH=CONFIG]247324[/ATTACH]
My question boils down to how do I force the redirection of the three urls to an internal HTTPS url so that the communications are secure? I've googled and come up with a bunch of links but none really seem to be what I am looking for.

Cheers

JMF

---

