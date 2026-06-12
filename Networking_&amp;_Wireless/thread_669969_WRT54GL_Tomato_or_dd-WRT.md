---
title: "WRT54GL Tomato or dd-WRT?"
date: 2008-01-16
forum: Networking &amp; Wireless
---

### Post by BrokenBrick on 2008-01-16
I was wondering if anyone around knows enough about Tomato or dd-WRT to answer me this. I want to abuse the fact that the building I live in is wired for double occupancy rooms, mine is a single, and use both of the wall jacks to basically double up my connection. So here is the gist of what I want to do.

EthPort1:Linksys WRT54GL wired to my raid array, ubuntu box, and windows workhorse
EthPort2:Netgear WGR614v6 unprotected wireless router to share my internet with the rest of the building and to dump extra bandwidth into my LAN through the Linksys

Not sure if this would be called a wireless bridge, or a multi-homed wireless/wired mesh, which is why I have had a hard time finding any info on how to set it up. Should I use Tomato for this or dd-wrt, or something else? Or is it possible at all? It's not that I necessarily want to use this for load balancing, I just basically want to use my Linksys as a normal Wireless client connected to the Netgear while it is also wired.

---

### Post by wieman01 on 2008-01-17
Frankly I don't think the set-up makes sense if this is about doubling your Internet bandwidth. I am not even sure if routers can handle multiple connections at a time (through wireless and Ethernet), but let's assume they can...

There'd still be the problem that both connections go through the same Internet gateway and that very gateway's maximum bandwidth is static and doesn't double simply someone tries to connect to it from different directions/computers. 

Do you get what I mean?

---

### Post by BrokenBrick on 2008-01-17
Makes sense to me.  I have heard of routers with two WAN ports but I suppose that is for load balancing or something that I don't really need.  I guess I'll just make my other router strictly a wireless gateway

---

### Post by wieman01 on 2008-01-17
Yes, I think that would be a better idea since you won't gain anything anyway. Interesting discussion nevertheless. :-)

---

### Post by BrokenBrick on 2008-01-17
Well I read somewhere that dd-WRT could manage multi-homed connections, but I assumed that I would have to crack open the router and do some soldering to turn one of the LAN ports into another WAN port.  Which is why I started to wonder whether or not I could wrangle in a wireless connection instead.  Once I get Tomato installed later I'll check it out:)

---

