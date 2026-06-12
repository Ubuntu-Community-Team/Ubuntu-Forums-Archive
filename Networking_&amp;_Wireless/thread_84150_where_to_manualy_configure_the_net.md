---
title: "where to manualy configure the net"
date: 2005-10-30
forum: Networking &amp; Wireless
---

### Post by senzacionale on 2005-10-30
Now i have DHCP with automaticaly ip adres. I want to add static 192.168.1.5 ip adress but i don't know where to add this. In gentoo is this in /etc/init.d/net but here is not this file.

So where i can fix that!

Thnx

---

### Post by cwaldbieser on 2005-10-30
[QUOTE=senzacionale]Now i have DHCP with automaticaly ip adres. I want to add static 192.168.1.5 ip adress but i don't know where to add this. In gentoo is this in /etc/init.d/net but here is not this file.

So where i can fix that!

Thnx[/QUOTE]
/etc/network/interfaces is the file you are looking for, I believe.

---

