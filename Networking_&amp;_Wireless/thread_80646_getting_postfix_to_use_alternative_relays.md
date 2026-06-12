---
title: "getting postfix to use alternative relays"
date: 2005-10-22
forum: Networking &amp; Wireless
---

### Post by dninja on 2005-10-22
I'm trying to get some emails routed through an ssl tunnel which maps port 22225 on my server to port 25 on the other end of the tunnel (don't ask why, long story). I want all mails going to *@lists.tp.int to go through this tunnel, so I've followed the instructions in:

[http://netmirror.org/mirror/postfix.org/transport.5.html](http://netmirror.org/mirror/postfix.org/transport.5.html)

and added the following line to my transport file

lists.tp.int      relay:[tb]:22225
.lists.tp.int      relay:[tb]:22225

I've ran postmap to create the db file and restarted postfix. All mails to the lists address still go through the normal relay.

Can anyone suggest anything I could have missed?

Thanks

---

