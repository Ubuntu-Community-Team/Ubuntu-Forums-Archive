---
title: "Router Recommendation for Static ip Blocks?"
date: 2017-08-01
forum: Networking &amp; Wireless
---

### Post by Robert_Boutin on 2017-08-01
Hi, I am changing my internet service from Uverse to WOW.  Each has a block of five usable static ip addresses.  My Uverse service comes with a Pace 5268AC Gateway that apparently is proprietary to Uverse.  But I can log into the gateway and assign static ip addresses to my four virtual servers through this gateway.

Changing to WOW, apparently I need to separate the modem and router.  I have a Motorola Surfboard modem that works fine.  But I need to buy a router that will let me assign multiple static ip addresses.

Can anyone suggest a router that is certain to be able to handle multiple static ip addresses?  I can't afford to keep buying a new router to find something that works.  I've checked the manuals from various routers on the market but the guides are pretty light in this area.  They all tend to say "If you have a static ip address (Rare)..."  I can't find anything yet that says definitively it will handle several static addresses.

Thanks so much for your suggestions.

---

### Post by #&amp;thj^% on 2017-08-01
I have used these two and highly recommend both.
[https://www.draytek.com/en/products/products-a-z/router.all/vigor2950/](https://www.draytek.com/en/products/products-a-z/router.all/vigor2950/)

This one is a bit spend y but worth a look.
[http://www.cisco.com/c/en/us/support/security/asa-5505-adaptive-security-appliance/model.html](http://www.cisco.com/c/en/us/support/security/asa-5505-adaptive-security-appliance/model.html)
We used it in our dealership. Seems you can find them on amazon also.
[https://www.amazon.com/Cisco-ASA5505-BUN-K9-ASA-5505/dp/B000O0Z8GC](https://www.amazon.com/Cisco-ASA5505-BUN-K9-ASA-5505/dp/B000O0Z8GC)

---

### Post by Robert_Boutin on 2017-08-07
Thanks for the suggestion.  I looked into both and they are a bit more than I was hoping to spend.  I asked the same question on Netgear's forum and one of the users suggested Ubiquiti EdgeRouter.  It looks like it will do exactly what I need for under $100.  I'll give that a try and see where I end up.  In the meantime, I'll mark this thread as "Solved" since you did give me something that would solve my dilemma.  Thanks

---

### Post by Robert_Boutin on 2017-08-20
So I bought the Ubiquiti EdgeRouter X about a week ago at MicroCenter (awesome store by the way) for $49 and while I have no experience configuring routers, this thing is awesome.  It took me about a week of after-work effort to get it configured to the point where I was confident enough to cut off Uverse and go live with WOW, but the Ubiquity forum (community.ubnt.com) is every bit as willing to help noobs like me as the Ubuntu forum.  Uverse's gateway is a 3-in-1 modem/router/wireless combined and I didn't realize how beneficial it would be to separate the three functions into individual devices until going through this exercise.  There is a lot more to configuring a router than I realized, mainly a result of having to NAT the public ip's to private ip's and having to gain some understanding of subnetting, so it's not for the faint of heart.  And I still haven't got my NAT loopback quite working, but I would be comfortable saying that anybody who has the basic competency to come onto this forum and make use of advice can also figure out how to configure the EdgeRouter to set up a better home or small office network.

---

