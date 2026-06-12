---
title: "Best approach to DNS changes for (staged) move to a new server"
date: 2024-07-30
forum: Networking &amp; Wireless
---

### Post by lister171254 on 2024-07-30
I'm currently running a mail server and a number of web instances on a single server.
I need to move all services to a new server and would appreciate your advice on the best approach to manage this move.

Let's call the domain mydomain.com
Let's call the old server old.mydomain.com with an ip addr of 1.x.x.x
Lets' call the new server new.mydomain.com with an ip addr of 2.x.x.x

The current DNS config is along the following lines
```
; A Record
@	600	 IN 	A	1.x.x.x
old	3600	 IN 	A	1.x.x.x


; CNAME Record
service1	3600	 IN 	CNAME	@
service2	3600	 IN 	CNAME	@
service3	3600	 IN 	CNAME	@
imap		3600	 IN 	CNAME	@
smtp		3600	 IN 	CNAME	@
```

I guess the first step is to ad an A record for the new server
```
; A Record
new	3600	 IN 	A	2.x.x.x
```

My question is to the best way to define the new CNAME records once I've moved the web instance given that mydomain.com still points to 1.x.x.x until everything has been moved and @ can point to 2.x.x.x?

Thanks

---

### Post by TheFu on 2024-07-30
When I'm going to change where services will be running, I change the DNS TTL from 1 week to 30 minutes or less, then wait a week for those changes to propagate.  A week later, I make the change, verify it is working (just need to wait 5 minutes), then slowly increase the TTL to 1h, 1d, 1w again.  I pay for DNS by the total number of queries, so a longer TTL helps keep my costs down.

BTW, I think it is a security risk to run email and web on the same OS instance, but that wasn't your question.

---

