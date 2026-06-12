---
title: "Destination unreachable, windows + ubuntu + router."
date: 2015-01-23
forum: Networking &amp; Wireless
---

### Post by aiasigia on 2015-01-23
Hello, 

I have my windows connected to a pc which is running ubuntu 14.04 that is connected to a wireless router. Basically I am using linux pc as a firewall with ids/ips. The problem is that when I play a game League of Legends in particular my windows machine starts sending echo requests to a game server and my ubuntu machine lets some echo requests through but the majority of them end up as Destination unreachable (Host Unreachable) messages via ICMP packets.When I connect to a wireles router  with windows machine these echo requests are sent without any problems. 
Some facts:
 Internet connection is shared from ubuntu to windows machine;
I have ufw firewall and snort.

I tried enabling icmp forwarding from my windows machine to gaming server and the other way round but there was no effect at all.
Disabling ufw did not improve this situation either.
I just wonder if this is entirely firewall problem or is there anything else involved. I live in a student dorm-like environment so that pc is necessary as firewall since i am not the only person using that router.

---

