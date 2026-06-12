---
title: "Yet another Remote Access Thread"
date: 2007-02-09
forum: Networking &amp; Wireless
---

### Post by MosesS on 2007-02-09
Apols for the repetitiveness but cannot find an answer after reading through most of the threads on here.

I want to access my home PC running ubuntu 6.10 from the outside world.

Up to now this is what I have done.

-installed ssh
-registered on dyndns
-created a script I found on the forum so that dyndns updates on its own
-registered the dyndns account details on my router which has a dyndns support

Problem...

1. by entering my domain name on firefox it takes me to my routers admin page

How can I get it to take me to my ubuntu desktop?

Cheers

---

### Post by kidders on 2007-02-09
Hi there,

> **MosesS said:**
> -created a script I found on the forum so that dyndns updates on its own
-registered the dyndns account details on my router which has a dyndns support
I'm not sure you needed to do both of those. (Won't they both do the same thing?)


> **MosesS said:**
> Problem...Think about what's happening from your router's perspective. Say it has 3 PCs connected to it, and a TCP packet arrives on port 25. It would have no way of knowing what to do with it. Usually though, routers have a NAT/packet forwarding configuration option that will let you forward services to individual machines behind its firewall.

Here's what to do:

[LIST=1]
[*]Now that you're registered with DynDNS, you'll start to notice a *lot* of unsollicited traffic. You _really_ need to disable all remote router administration, before someone decides to have some fun with your internet connection!
[*]See if your router configurator knows anything about NAT/port forwarding, and redirect port 80 to your Ubuntu box. Don't redirect more ports than you actually need.
[*]Make sure your web server is listening on the network interface connected to your router.
[*]Make sure Ubuntu isn't running anything (eg a firewall) that would prevent incoming connections on port 80 being accepted.
[/LIST]

I hope that helps.

---

