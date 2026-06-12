---
title: "Networking connection issue.  Sort of."
date: 2008-12-04
forum: New to Ubuntu
---

### Post by myolbug on 2008-12-04
I have an internet connection but I am just wondering.  I am running Ubuntu 8.10, which is SLOWER than 8.04, by the way.  Anyway, on the upper right hand corner, there is an icon for networking connection.  It has a triangle with an exclamation mark on it.  When I right click it, it says that there are no internet connections, but as you can tell I am connected.
  
Basically a non-issue, but I thought that I would ask.  I am running through a wired router, if that makes a difference.  The security measures are set up pretty high, 'cuz I am weird like that.

Any ideas?

---

### Post by conscious on 2008-12-04
This is the icon of Network Manager applet. You internet connection was probably configured without the help of the NM, so it thinks there are no connections. (Which is the case for me - I have configured my connection by editing /etc/network/interfaces and /etc/resolv.conf)

---

### Post by myolbug on 2008-12-04
Spasibo!  I didn't think it was too big of an issue, but I was curious.

---

### Post by billgoldberg on 2008-12-04
> **myolbug said:**
> I have an internet connection but I am just wondering.  I am running Ubuntu 8.10, which is SLOWER than 8.04, by the way.  Anyway, on the upper right hand corner, there is an icon for networking connection.  It has a triangle with an exclamation mark on it.  When I right click it, it says that there are no internet connections, but as you can tell I am connected.
  
Basically a non-issue, but I thought that I would ask.  I am running through a wired router, if that makes a difference.  The security measures are set up pretty high, 'cuz I am weird like that.

Any ideas?

How exactly is Ubuntu 8.10 slower?

We might help you speed it up, but it would be better to open a new thread about it.

---

### Post by superprash2003 on 2008-12-04
post output of ifconfig from terminal

---

