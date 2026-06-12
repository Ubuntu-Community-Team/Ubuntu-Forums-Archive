---
title: "how to change DNS settings?"
date: 2005-05-18
forum: Networking &amp; Wireless
---

### Post by WildTangent on 2005-05-18
i determined what was wrong with my friends internet access. he can access and ping IP #s, but not website addresses, so its a DNS name server problem. but i dont know how to fix this. hes got DSL internet from Bell Sympatico, on a Dlink DI-604 router. this is my friends first venture into linux, and id like the experience to be enjoyable for him, because if he isnt impressed, hell never try it again (hes just that kind of person i guess  :? )

-Wild

---

### Post by alastair on 2005-05-18
What is set in the /etc/resolv.conf file?

DSL routers sometimes have a caching nameserver, so you can set the "nameserver" to be the router IP e.g.

nameserver 192.168.0.1

Assuming the router is 192.168.0.1.

Otherwise, you need real nameservers in there - from Bell probably (who should have told you their addresses).

---

### Post by WildTangent on 2005-05-18
k, seems he was able to fix it himself, delete this thread mods if you want

-Wild

---

