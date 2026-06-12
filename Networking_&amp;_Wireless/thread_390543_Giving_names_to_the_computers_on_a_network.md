---
title: "Giving names to the computers on a network"
date: 2007-03-22
forum: Networking &amp; Wireless
---

### Post by Nighto on 2007-03-22
Hi,
i have three computers on a network, and i usually copy lots of files between them. Usually i have to type something like "scp user@192.168.0.1:~/file user2@192.168.0.2:~/folder". 

Instead of doing so could i nickname them, like "ssh user@server" or "ssh user@notebook"? How could i do that?

---

### Post by MrCheese on 2007-03-22
> **Nighto said:**
> Hi,
i have three computers on a network, and i usually copy lots of files between them. Usually i have to type something like "scp user@192.168.0.1:~/file user2@192.168.0.2:~/folder". 

Instead of doing so could i nickname them, like "ssh user@server" or "ssh user@notebook"? How could i do that?

Put entries in the /etc/hosts file.....

so for instance

192.168.0.1 router       router.home
192.168.0.2 pc1           pc1.home
192.168.0.3 pc2           pc2.home

so - address, nickname, full name (nickname + domain name, if you have a domain name for your home network)

You can then use the machine nicknames instead of addresses.

---

