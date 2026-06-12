---
title: "I stumped a CCNA with this!"
date: 2008-03-25
forum: Networking &amp; Wireless
---

### Post by SpooBoy on 2008-03-25
I stumped a CCNA last week with this question so I thought I would try my luck here.

I have 3 computers set to static "10.170.0.x" behind my WRT54G v5. The WRT54G is aquiring it's ip from my 5x1mb motorola Residential cable modem with DHCP. 

I also have a second 5x1mb motorola "Static" Business cable modem for my home office that's running stright to a 4th computer that's not connected to the formentioned LAN of 3 computers.

So what I have is a LAN of 3 with it's own DHCP modem and a 4th computer with it's own STATIC modem.

What I would love to do here is be able to join all 4 computers together for the purpose of filesharing and (dare I say) gaming while making sure that the LAN of 3 continues to use the Residential modem and the 4th computer continues to use the Static Business modem even when all 4 computers are on 1 LAN.

I have put a second NIC in the Business computer and configured the NIC card without a Gateway and without DNS and gave it an IP in the 10.170.0.x range of the Residential LAN. I connected that second NIC to the WRT54G with the intention of creating a LAN with the 4 computers while keeping the first 3 computers on the residential modem service and the 4th computer on the Static Business modem.  Long story short....it ain't be working.

I hope I explained this correctly. Any help would be awesome. Thanks guys.

---

### Post by Whiffle on 2008-03-25
Hmm, sounds like it should work.  What doesn't work exactly?  Can anything get internet?  Can they ping each other?

---

### Post by IsawSp4rks on 2008-03-25
What are the DNS settings for each of the NICs in the 4th PC?

---

### Post by saydinli on 2008-03-25
Ok , what is happening here is that your 4th PC doesn't know how to get to the 10.170.x.x network because it has no gateway associated with it. So If you want this to work you need to add a static route to this pc pointing all traffic destined to your home LAN to use the 2nd NIC. As it stands the 4th PC is using its known default gateway (the static modem) to send all traffic to you local LAN and of course it can't route to your local LAN through your ISP.

So if its a Windoz box you would need an entry something like this :

from a command prompt

route ADD 10.170.0.0 MASK 255 255.0.0 10.170.x.1 IF 2

*( the 10.0.179.x.1 is assuming this is the IP of your home LAN router)
** ( IF 2 is the interface ID of your 2nd NIC)

do a route PRINT after and you should see the route added and it should be using the interface with IP of 10.170.x.x

Hope this helps.

---

