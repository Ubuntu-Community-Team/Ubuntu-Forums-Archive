---
title: "smtp relay"
date: 2007-11-30
forum: Networking &amp; Wireless
---

### Post by SaltyCrak on 2007-11-30
how's this for a network setup...

i have an 8mb line for surfing and connecting to clients, a 64k dsl line that is dedicated to the mail server, a 10mb/s line connecting to one of my isp's (hosting my website), a 512k line connected to my biggest client vial vpn. 
to control all the routing and fire wall rules, i have a pfsense machine (i tried doing this with linux, but it's damn diffucilt) that does all the natting/routing/firewalling.

everything is wok\rking perfecly except for the fact that my exchange box is open on 25 and i'm being used as a smtp spam relay. 

how can i prevent those spam fukkers from using my exchange server as a smtp relay?

i've tired many configuration options in exchange, but the mail queue remains huge!

spam is not leaving my office due to firewall rules i havw in place, but it's still coming in and s.owing down my exchange bos. 

any advice would be much appreciated...

thank you
kev.

---

### Post by SaltyCrak on 2007-11-30
oh, by the way...
i know this seems like it has nothing to to with ubuntu, but seeing as i'm getting used to this beautiful OS, i thought that there might be a tool that i could use. 
maybe put a box in between my pfsence firewall and internal network that could sort things out. 
cheers

---

