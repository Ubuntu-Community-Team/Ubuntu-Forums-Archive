---
title: "[SOLVED] for what EXACTLY do i need dnsmasq?"
date: 2008-07-03
forum: Networking &amp; Wireless
---

### Post by moore.bryan on 2008-07-03
well, pretty simple. i have a very simple system and i want to know why i need dnsmasq. i've tried to find-out more about it, but the information is either FAR above my head or completely unhelpful.

---

### Post by SpaceTeddy on 2008-07-04
dnsmasq is a small utility that allows other computer to query your computer for dns records. 

normally, when you visit a website (let's be imaginative and use ubuntuforums.org) your browser will first query a dns server to figure out what ip the is behind ubuntuforums.org. Once it has figured that, it will then send a request to the webserver on that IP (**NOTE**, this is NOT the name !!!).

So, for viewing this site you need the dns server. Sometimes it is impractical or overhead to run a full blown dns server on a system. For example, in your home network you don't need any dns server, as there are no dns names known in your own network. All you need are the dns names of the internet, which are running somewhere on the internet. So, either you tell every client where the internet DNS server are, or you run dnsmasq on the little router box. Then every client in your home network can query the router - which does not know anything about the dns records itself, but will instead just forward your request to it's own dns servers. When the reply comes back, it will hand it down to your client. 

Hope it helps :)

---

### Post by moore.bryan on 2008-07-04
excellent explanation, spaceteddy.

so, to follow your input, with my laptop on my home wireless network and NO computers trying to connect to may laptop, i would have NO NEED whatsoever for dnsmasq; correct?

---

### Post by SpaceTeddy on 2008-07-04
yep, if your laptop does not get queried for dns requests from other computers, you don't need dnsmasq. 

Also, if your laptop only need to ask dns server (query itsef), the /etc/resolv.conf is totally sufficient :)

---

### Post by kevdog on 2008-07-04
Your laptop however could cache dns requests, so that in the future  it would simply query the cache rather than the DNS server for the IP address.  Cached dns requests should speed up the process.

---

### Post by moore.bryan on 2008-07-04
> **kevdog said:**
> Your laptop however could cache dns requests, so that in the future  it would simply query the cache rather than the DNS server for the IP address.  Cached dns requests should speed up the process.
however, aren't my dns queries cached WITHOUT dnsmasq?

---

### Post by SpaceTeddy on 2008-07-04
depends on your setup. Normally, no, they are not cached on your machine. But your router connected to the internet will cache them, as most of them have dnsmasq running anyway. I don't really see a benefit for caching on the machine as well as the router. And even if you don't cache, dns queries don't use a lot of bandwidth, don't linger in the ip stack table (as they use udp) and the dns servers you are given are usually from your ISP and reachable fast. So - you'd probably gain about 100 ms on the request. Maybe a little more. 

Seriously, for a home network i would not worry about it. But that is me...

---

### Post by moore.bryan on 2008-07-05
well, i've uninstalled it and have seen absolutely no adverse effects, which also begs another question: why would ubuntu have this installed and running, by default, on install?

---

