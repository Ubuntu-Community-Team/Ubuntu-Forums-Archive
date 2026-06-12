---
title: "LAN-only webserver"
date: 2007-11-13
forum: Networking &amp; Wireless
---

### Post by rplantz on 2007-11-13
I am trying to set up a webserver that is only visible on my LAN: Ubuntu, Mac OSX, Windows machines. My goal is to learn more about creating websites.

I've installed apache, mysql, and php. I feel like I'm almost there, but I'm hazy on a few points.

1. How do I specify a "domain name" for my LAN?

2. I connect to the outside world through a router. I use DHCP with my ISP and my local machines. Can I continue using DHCP for my local machines, or should I assign them static (local) IP addresses?

3. Can I effectively create more hosts by using the virtual host feature of apache?

I've been doing lots of reading and think I have a fairly good idea of how to do this. But it would be nice to get some pointers to howto's, etc. to check my thoughts before actually doing it.

---

### Post by Fire_Chief on 2007-11-13
> **rplantz said:**
> 1. How do I specify a "domain name" for my LAN?
If you mean how do you configured a whatever.com or something.net address for your LAN, what you'd typically want to do is setup a DNS server for your local network. I would recommend using a non-public DNS suffix though like .prv (would suggest .local but you'd run into issues with the OS X box). As far as the name, you could call it anything (lan.prv, home.prv, mynetwork.prv, etc.). Create A records for the local server on the DNS server.Then you have your workstations point to the local DNS server for resolution and have the DNS server forward requests it can't answer to external (Internet) DNS servers.

> 2. I connect to the outside world through a router. I use DHCP with my ISP and my local machines. Can I continue using DHCP for my local machines, or should I assign them static (local) IP addresses?
Yes, you can still use DHCP for the workstations but I would set a static IP on the webserver (choose an address that won't get handed out by DHCP).

> 3. Can I effectively create more hosts by using the virtual host feature of apache?
If by "hosts" you mean additional websites, then yes. The virtual host feature lets you have multiple websites which all share the same IP address. Apache uses the domain name of the individual website to figure out which one you want to get to.

---

