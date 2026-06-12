---
title: "Dymanic DNS update"
date: 2008-02-09
forum: Networking &amp; Wireless
---

### Post by ambre on 2008-02-09
Hi guys,

Here's the picture:

I have an Ubuntu server (7.10) with a static IP address running BIND9 and SAMBA.  SAMBA is set up as a WINS server.

I have a LAN of WINXP Home machines receiving dynamic IP addresses handed out by my Belkin router.

All WINXP machines can ping themselves, each other and the server by both IP and name.  However, the server can ping itself and everyone else by IP address but only itself by name.

How can I get the Ubuntu server to resolve dynamic local machine names?

Thanks,
Fred

---

### Post by kevdog on 2008-02-09
Did you install winbind?

---

### Post by ambre on 2008-02-09
Short answer - NO.  Is this the missing link?

Thanks,
Fred

---

### Post by kevdog on 2008-02-09
Take a look at this entire thread:
[http://ubuntuforums.org/showthread.php?p=1770797#post1770797](http://ubuntuforums.org/showthread.php?p=1770797#post1770797)

---

