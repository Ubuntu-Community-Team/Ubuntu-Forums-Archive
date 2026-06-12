---
title: "DNS keeps going back and forth"
date: 2006-12-10
forum: Networking &amp; Wireless
---

### Post by themoebius on 2006-12-10
This isn't an Ubuntu specific question so sorry if its in the wrong place.

I updated the DNS records of a domain yesterday because I just ordered a new virtual private server for hosting. So I set in the host summary ns1.mydomain.com and ns2.mydomain.com to point to the IP address of my new server and then set the name servers to ns1 and ns2.mydomain.com. I think all of that is correct.

When, then, could the reason be for the forwarding to keep switching back and forth between the old server and the new? When I ping the domain it goes to the correct place then maybe 10 minutes later it goes to the old place and a while later it will go to the correct place again, etc, etc.

I'm behind the router, but I've specified the DNS numbers manually in network settings so I don't think the router would make a difference but maybe I'm wrong.

Any ideas for the cause of this?

---

### Post by Iowan on 2006-12-11
Can you set DNS settings in router, too (or instead)?

---

### Post by themoebius on 2006-12-11
I got it sort of figured out. Apparently neither my new DNS or my old DNS server was authoritative and there was some kind of problem with my new DNS that made it refer to the old one at times which caused it to flip back and forth.

This dnsreport.com site gives you a list of all the crap that is wrong or right with your domain.

---

