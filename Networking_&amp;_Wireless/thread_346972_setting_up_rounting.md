---
title: "setting up rounting"
date: 2007-01-26
forum: Networking &amp; Wireless
---

### Post by voltage on 2007-01-26
Hi,

may I know how to add round permanently, because I have try to sudo route add -net  192.168.0.1 netmask 255.255.255.0 dev eth0. But after I restart the Ubuntu, then the routing table is lost.

So do anybody know how to set the routing table permanently?

Thanks and good day..

---

### Post by zubrug on 2007-01-26
Don't laugh but I discovered this by accident, goto sessions and startup in preferences, select save session on exit, set up your connection, then simply unplug your computer (as in a power outage, thats what happened to me and ever since it has worked on every boot) replug and start, good luck. Not positive if you have to set save session but I had it set.
This has worked for me in edgy and feisty testing, stop laughing already.

---

### Post by voltage on 2007-01-26
> **voltage said:**
> Hi,

may I know how to add round permanently, because I have try to sudo route add -net  192.168.0.1 netmask 255.255.255.0 dev eth0. But after I restart the Ubuntu, then the routing table is lost.

So do anybody know how to set the routing table permanently?

Thanks and good day..

Hello ... any experts can giving me any hints from above ?

---

### Post by chipmonk010 on 2007-01-27
sudo gedit /etc/network/interfaces

add theses 2 lines at the bottom of your eth0 section

up route add -net 192.168.0.1 netmask 255.255.255.0
down route del -net 192.168.0.1 netmask 255.255.255.0

---

