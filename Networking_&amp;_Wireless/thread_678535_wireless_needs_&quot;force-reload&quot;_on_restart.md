---
title: "wireless needs &quot;force-reload&quot; on restart"
date: 2008-01-26
forum: Networking &amp; Wireless
---

### Post by TehCamel on 2008-01-26
I've got an install of 7.10 dual booting with winxp on my Inspiron 510m.

I use wireless as a preference, and the onboard 10/100 nic is disabled in the bios based on this. (When enabled, it does work however)

What I've found is that any time I restart, the wireess networking just isn't working. I need to open a command prompt and run /etc/init.d/network force-reload

I've checked it out before now, and even before running th force reload, the interface is active and iirc, is uhm whats the word... assigned.. ? to the wap, it just can't resolve names, or ping the ip of the router.
doing a force-reload solves it.

I DO have auto eth1 in /etc/network/interfaces and i'm not sure what else I can look at. any suggestions ?

---

### Post by luisromangz on 2008-01-26
Maybe your setup has a conflict with NetworkManager. You speak of having your network configured through /etc/network/interfaces, I use NetworkManager and no config in this file is required.

---

