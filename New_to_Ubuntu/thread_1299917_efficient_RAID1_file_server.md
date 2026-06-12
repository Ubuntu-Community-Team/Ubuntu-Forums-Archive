---
title: "efficient RAID1 file server"
date: 2009-10-24
forum: New to Ubuntu
---

### Post by pcmacd on 2009-10-24
I need to put together a RAID1 file server for use by Windoze systems. I've built zillions of windows systems from components. I was a HPUX SE for a long time at HP, but have been out of the UNIX world for years.

I've got an old workhorse mobo FIC PA-2013 with a 450 MHz K6 III+ I could use, but I'd need to get a RAID card for that.

I've also got a PCCHIPS M789 mobo with the VIA C3 processor, but would still need a RAID card.

It occurred to me that if I need to buy a RAID card I might be better off buying a new MOBO with the raid built in with a second or third tier efficient processor.

I won't be doing video editing over the LAN which is currently 100 BT.

I would like a balance between performance and operation cost (ever calculate what 500 watts costs for 24x7?) 

I would appreciate recommendations for both hardware and flavor of LINUX.

I realize that there may be posts here relating to this topic, but I haven't stumbled upon any.

tanksAbunch

pc

---

### Post by QLee on 2009-10-24
I would suggest you go with software raid. ...Or, buy two raid cards exactly the same. People have made headaches for themselves when a raid card went down only to find that a different raid card wouldn't work after the replacing the failure. The *nix software raid works well, doubt that you'd have any speed issues.

---

### Post by pcmacd on 2009-10-27
> **QLee said:**
> I would suggest you go with software raid. ...Or, buy two raid cards exactly the same. People have made headaches for themselves when a raid card went down only to find that a different raid card wouldn't work after the replacing the failure. The *nix software raid works well, doubt that you'd have any speed issues.

Thanks for your reply.

Not sure what you mean by "The *nix software raid"?  Generic UNIX software raid?

If disaster recovery is important (why would it not be??) I see your point.

!!!!!!!!!!

So, going with a software RAID1, I suppose the MOBO and processor are not an issue?

Perhaps I should just go with one of the existing hardware sets I have and see how it goes?

Thoughts and comments, if you please.

tx

pc

---

