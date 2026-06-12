---
title: "Using multiple dialup connections at the same time"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by adewale on 2007-04-24
i am able to browse on my pc using wvdial but there's an extra phone and i was wondering if it was possible to also create a connection for it and use both connections at the same time. would it increase the speed? thanks

---

### Post by bnuytten on 2007-04-24
Interesting question. You can use multiple Ethernet interfaces as one to increase speed. It is called interface bonding. BUT you also have to configure the switch to use "bonding", teaming or whatever you want to call it.

So... for dial-up connections... I honestly do not know since I do not use these. I however have a similar setup using broadband modems. Two interfaces, two seperate lines. I only use one of them at a time. You would have a routing problem anyway. The default route can only point to one of the lines. You can use metrics so the other line acts as a backup but that will not improve your speed.

There may be a solution and it is called load-balancing. It would take me to far to explain all the details so I'll try to keep it short. Connection 1 is send via line A, connection 2 via line B, 3 via A, 4 via B... You get the idea? ;-) It is quite difficult to setup :-) Look for IP Virtual Server Admin (ipvsadm).

---

### Post by adewale on 2007-04-24
thanks i'll try that and whatever happens i'll let you know.

---

