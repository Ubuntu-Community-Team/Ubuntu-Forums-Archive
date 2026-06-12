---
title: "Internet Sharing"
date: 2007-09-30
forum: Networking &amp; Wireless
---

### Post by Alien56 on 2007-09-30
I have a crossover cable and I was wondering if it is possible to share an internet connection from Windows XP to Ubuntu? Im using Ubuntu 7.04.

---

### Post by R!nGo on 2007-09-30
same here :mad:

---

### Post by helgman on 2007-10-04
Yes it is, provided you have two network cards on the Windows XP computer.

If I remember correctly you just right-click the connection you want to share (the one going to the Internet) and then that part should be done. You'll find a better description of it [here](http://support.microsoft.com/kb/306126) (Microsoft).

Then you have to configure the Ubuntu machine to use the internal IP address of the Windows machine as it's gateway.

And don't forget to setup DNS (not a server).

If you need further instructions please let me know with a little more specific information about the problem.

Regards,
Helgman

---

