---
title: "TCP accept connecton limit?"
date: 2007-05-05
forum: Networking &amp; Wireless
---

### Post by jafa on 2007-05-05
Hi guys,

I am hitting a tcp connection limit on my Ubuntu server (Edgy).

The application is listening on one TCP port and will accept the first 1015 connections ok. 
Subsequent connections will fail (accept returns error) until some of the previous connections are closed, again always stopping at 1015 connections.

proc reports 1080 total connections so I figure it must be a per port/listening socket limit?

Any ideas where this limit is configured so I can increase the limit?

Thanks,

Nick

---

### Post by jafa on 2007-05-05
I think I just answered my own question - it looks like the limit is set by the listen() function.

Nick

---

