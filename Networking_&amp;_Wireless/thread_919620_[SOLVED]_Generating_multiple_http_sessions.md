---
title: "[SOLVED] Generating multiple http sessions?"
date: 2008-09-14
forum: Networking &amp; Wireless
---

### Post by fwre01 on 2008-09-14
I was wondered if anyone had any thoughts on how i could create multiple http sessions from one single host to a website via a script?

I need to test a load balancer, but need a way of generating enough sessions to analyze how the load balancer is distributing the tcp sessions across my real servers.

I'm about to start reading the links manual, maybe i can define a source port when accessing the site and then just repeat that in a bash script. But thought i would ask the question in case anyone has done such a thing in the past. Thanks :)

---

### Post by fwre01 on 2008-09-14
OK, iv found a program called siege that can do exactly that. :-)

---

