---
title: "Why there're two servers in http HEAD request?"
date: 2015-05-30
forum: Networking &amp; Wireless
---

### Post by papakota on 2015-05-30
Hello!

I use Ubuntu Desktop's terminal where I type the following command:

HEAD [sitename.com...] HTTP/1.1

In the reply I see one server, say, for Google it could be gws or most  of the time it's nginx and then below that, there's Apache. How come  there're 2 of them for one site?

---

### Post by Lars Noodén on 2015-05-30
Can you post the full set of headers?  It will be easier if we see what you see.  It could just be a redirect from one address to another.

---

### Post by papakota on 2015-05-30
Here's a screenshot...

---

### Post by SeijiSensei on 2015-05-30
Probably there's a gateway server (hence the name "gws") running in reverse proxy mode to distribute the load.  You connect to that, then it passes your connection to one of the pool of servers behind it.  Just a guess though.

---

### Post by papakota on 2015-05-30
> **SeijiSensei said:**
> Probably there's a gateway server (hence the name "**gws**") running in reverse proxy mode to distribute the load.  You connect to that, then it passes your connection to one of the pool of servers behind it.  Just a guess though.

Doesn't it stand for **G**oogle **W**eb **S**erver???

---

### Post by SeijiSensei on 2015-05-30
Who knows?  You said that sometimes it's replaced by nginx.  I still think it's a proxy regardless of what it is called.

---

### Post by papakota on 2015-05-31
Thanks for your reply, but I still don't understand. If the site physically resides on gws or nginx, then why we have another type of server.

---

### Post by SeijiSensei on 2015-05-31
[http://en.wikipedia.org/wiki/Load_balancing_%28computing%29](http://en.wikipedia.org/wiki/Load_balancing_%28computing%29)

---

### Post by papakota on 2015-05-31
I see... Okay, thanks for your reply!

---

