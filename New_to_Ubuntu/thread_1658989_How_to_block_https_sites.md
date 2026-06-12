---
title: "How to block https sites?"
date: 2011-01-03
forum: New to Ubuntu
---

### Post by karthick87 on 2011-01-03
I know the way to block to http sites..Can anyone say me the way to block https sites?I dont want to block all the https sites,i want to block only a few sites..

---

### Post by endotherm on 2011-01-03
> **karthick87 said:**
> I know the way to block to http sites..Can anyone say me the way to block https sites?I dont want to block all the https sites,i want to block only a few sites..
well, just drop packets to those specific sites on TCP port 443. you will have to specific each site individually however. you can only filter https traffic on information contained in the transport layer header or below. everything above that is encrypted.

---

### Post by Gone fishing on 2011-01-03
Why are you blocking sites?

I block sites for access by our school network using squid proxy server and an squid guard. 

You have lots of blocking options.

---

