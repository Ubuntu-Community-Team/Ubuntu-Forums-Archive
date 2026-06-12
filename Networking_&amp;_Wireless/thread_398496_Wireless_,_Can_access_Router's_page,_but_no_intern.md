---
title: "Wireless , Can access Router's page, but no internet?"
date: 2007-04-01
forum: Networking &amp; Wireless
---

### Post by lonekiewie on 2007-04-01
Hello, I am very new to linux,

I just installed a fresh copy of ubuntu 6.10, and configured the network to connect to my wireless router and view other computers on my network. On my other windows PC's I can connect to the internet fine. On this linux pc, I can only communicate with my router, but I cannot get onto the internet.

I'm using an Atheros Communications based network card. Help appreciated

---

### Post by lonekiewie on 2007-04-01
Sorry double post.

---

### Post by lonekiewie on 2007-04-01
Even stranger, I can ping [www.google.com](www.google.com) , yahoo.com, with a hefty 200 + ms time. But I still cant browse any websites or connect to gaim.

---

### Post by Rui Pais on 2007-04-01
if you can ping a site but can't browse there you must probably have a problem with DNS.

Try to do [this]("http://www.opendns.com/start/unix.php") to see if it solves the issue.

If that don't solve it, the next thing you should check is if ipv6 it's not the guilty one.

---

### Post by lonekiewie on 2007-04-01
Thank you very much Rui Pais,
it appears ipv6 was guilty :)

---

### Post by Rui Pais on 2007-04-01
> **lonekiewie said:**
> Thank you very much Rui Pais,
it appears ipv6 was guilty :)

Usaully is :)

I'm glad its working,

have fun.

---

