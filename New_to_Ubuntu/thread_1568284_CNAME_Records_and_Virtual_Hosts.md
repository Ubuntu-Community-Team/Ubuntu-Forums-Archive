---
title: "CNAME Records and Virtual Hosts"
date: 2010-09-05
forum: New to Ubuntu
---

### Post by adamjkok on 2010-09-05
My IP is dynamic, and lately it's been more dynamic than ever, changing every couple of days or even *hours* instead of months. I have a bunch of .TK domains and misc. subdomains pointing to this IP using an A record, and it's a pain in the **** to change everything all the time.

So let's say that I have two domains. "pointer.example" points to my IP using an A record and "site-a.example" points to "pointer.example" using a CNAME record. The virtualhost file says that the host is "site-a.example:80" (I can't use port 80 because my ISP sucks and decided to block inbound connections on it, but we'll use this in our example to simplify the problem)

If a visitor types site-a.example, would he/she be sent to the right place or would the server interpret the request as "pointer.example:80" and not display the website?

---

