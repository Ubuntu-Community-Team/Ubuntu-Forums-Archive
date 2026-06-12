---
title: "LAST_ACK connections problems"
date: 2007-09-25
forum: Networking &amp; Wireless
---

### Post by jackharrer on 2007-09-25
When I use Azureus (sharing only, legal stuff so I don't expect an attack) sometimes it builds up a lot of connections stuck on LAST_ACK - up to 1000. That slows down computer terribly. Is there a way of setting timeout for those connections to something shorter than current forever?

I will not post the output of netstat -na as people who know what's going on will know it anyway. All connections stuck on LAST_ACK are tcp6 ones.

Even if I kill Azureus (as it's impossible to close it, computer's too unresponsive) it doesn't close the ports it opened using UPnP thus allowing those connections to be still created.

BTW: it occurs on Ubuntu Feisty Server.

---

### Post by jackharrer on 2007-09-29
Anybody knows how to sort it out?

---

