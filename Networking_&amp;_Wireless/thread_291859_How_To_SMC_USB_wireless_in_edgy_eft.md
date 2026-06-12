---
title: "How To: SMC USB wireless in edgy eft"
date: 2006-11-03
forum: Networking &amp; Wireless
---

### Post by homy06 on 2006-11-03
I figure I'd try giving something back to the community

I have a smc usb wireless adaptor and it worked in dapper magically with ndiswrapper.

When I upgraded to Eft, errrrrwwit, network manager didn't detect my wireless even though ndiswrapper said it was fine. I tried everything and a no go.

What I ended up doing to solve it and its really actually quite simply. I did a fresh install of edgy eft, then I downloaded the ndiswrapper from synaptic and MADE SURE I GOT THE UTIL 1.8, (doesn't come automatically must click on it) and then I went into 
/etc/network/interfaces/ and deleted everything but the first two lines. 
so it looked like this



auto lo
iface lo inet loopback


and then i rebooted, and viola like magic. everything worked. 

so yea I hope it helped someone out, i know smc usb adaptor users must be a minority

---

