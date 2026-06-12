---
title: "Two gateways, four DNS servers"
date: 2007-06-07
forum: Networking &amp; Wireless
---

### Post by onosenday on 2007-06-07
Hi,
I've a net with two gateways, one internal for all the locations of the internal net at work and another (faster) for internet.

I want to know if there's a way to configure the routing table for redirect all the internal traffic to one gateway using two DNS servers and other gateway for internet using other differents DNS servers without having to setup diferents locations in the network manager.

Some tips for a newbie???


PD: I'm spanish, my english is only "spanglish", Sorry!!! :-D

---

### Post by Mr. C. on 2007-06-07
Routing and DNS are two separate things.

You can add entries into your route table (man route) for your internal networks, so that all internal traffic stays internal.  

You can add a default route for all other (internet) traffic.

You can only use 1 DNS server however, regardless, as the resolver library used by networking applications only uses one, unless failure, whereby it uses the secondary, and tertiary servers if configured and available.  There can be backup DNS servers configured, but they are only used after 15 second timeouts, which is not a solution to your problem.

You can uses hosts files, NIS, NIS+, WINs, or other directory service before DNS queries, which would allow you to use, for example, /etc/hosts before DNS is tried.

Otherwise, you will need to run your own DNS server.  It can be authoritative for your internal domains, and can either forward requests to your ISPs DNS servers for all other queries, or it can resolve them itself.  This is not difficult.

MrC

---

### Post by onosenday on 2007-06-07
Thanks for the quickly reply!!!
As I've said I'm a newbie...
I can use HOSTS because i only know the destination net and the net where i am
The gateway for the first and the gateway for internet are in my net and all the services that can access on the destination net are resolved by the dns servers on it and the internet DNS servers are external (ISP provided) so i can't figure how my own dns server can help me to resolve directions...

A little more help??

Thanks again!!

---

### Post by Mr. C. on 2007-06-07
Sure, no problem.

I'm not sure what you mean "destination net and net where I am".  We need to use more specific networking terms, and let's use network IP addresses to do that. 

Start be listing the main systems involved (don't care what type they are, except for the linux box you are trying to configure), your network IP info (eg network address, netmask, etc.) for each net / subnet, and explain the basic connections. to/from each.  We need to know:

If it is too complicated for you to explain in words, you can draw a quick diagram, scan it, and post it here.  Or you can use simple ascii art pictures.   Label the connections and their network addresses.

MrC

---

