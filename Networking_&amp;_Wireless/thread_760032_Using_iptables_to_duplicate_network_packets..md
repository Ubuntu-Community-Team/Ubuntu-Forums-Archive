---
title: "Using iptables to duplicate network packets."
date: 2008-04-19
forum: Networking &amp; Wireless
---

### Post by CrazyGuy123 on 2008-04-19
I have an odd problem - a network link with 20 - 25% packet loss that is totally independant of load.  I have no control over the link so I can't fix the root of the problem so I'm looking for a workaround.

I looked at wikipedia and figured that because TCP discards duplicate packets, if I could find a way to duplicate every packet, then the chance of both the original and duplicate packet going missing is 0.25*0.25= ~6%, so by duplicating every packet I should see a big increase in performance.

I guess iptables can do this, maybe with the --tee option, but I'm not sure how to do it.

Really I want to make this machine take every packet that it would have sent through eth0, duplicate it, and then send both the original and the duplicate down eth0.  The machine isn't a router, so only packets from local applications matter.

Will duplicating UDP packets also work, or will it confuse applications?  (I'm thinking mainly about DNS)

---

### Post by CrazyGuy123 on 2008-04-20
spent a while googling for this, and I still don't know how to do it.  My google searches indicate I might need to patch iptables and recompile the kernel - I guess I should ask that on a mailing list and not here though...

---

