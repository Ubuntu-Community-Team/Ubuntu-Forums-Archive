---
title: "how to add a switch to my router"
date: 2007-11-21
forum: Networking &amp; Wireless
---

### Post by ginestre on 2007-11-21
I have a Netgear DG 834GT hub + ADSL router that connects my bits of kit to each other and to the internet. The router  does internal NAT translation, ADSL connectivity and firewalls. The bits of kit are 3 ubuntu PCs, a Windows98 PC, and a network printer, so at the moment I plug and unplug into the router- I have 5 bits of kit and the router only has four holes. 

Now I need even more plugholes than the router provides - not only am I tired of plugging and unplugging, I also now need to plug both the old hitherto unconnected laptop and a new ubuntu PC, as well as a VoIP phone. 

Can I just simply get a multiple hole switch, and plug it into one of the holes on the router, effectively putting more holes through one router hole? Are there difficulties and limitations, or points I need to be aware of and watch? How would this affect NAT?

If I can simply do this, can I use any old switch whatsoever, as long as it's 10/100 ethernet which is what the router supports, or should I get one thing rathre than another? Could I even use an old 16 port switch I  have inherited from somewhere or other, and so not spend any of my very scarce money at all?

Thanks for your help, and your time

---

### Post by AlanRogers on 2007-11-21
The short answer is yes, you can use any old switch. When you plug it's uplink port into your router using a straight (not cross-over) Cat5 cable, it should pick up an IP address and go live, assuming you are using your router as a DHCP server.
 
I'd recommend plugging one working computer directly into the router and another into the switch, with the switch plugged into the router as suggested. Then, try connecting to the internet on both.
 
If you get pages on both, well done - it's all working. If you only get them on the router-connected computer, you know that the problem is between the router and the other computer; it might be the switch.

---

### Post by ginestre on 2007-11-21
Alan- thanks for that very encouraging reply- and most particularly for the tip about the straight not crossover cable, which I wouldn't have thought of, and which would almost certainly have totally bewildered me when nothing worked with the crossover cables I would have unknowingly used....

---

