---
title: "Firewall help: Radmin-port getting hammered"
date: 2005-08-17
forum: Networking &amp; Wireless
---

### Post by wadesmart on 2005-08-17
08172005 1611 GMT-5

I have firestarter as my firewall and under Events for the last 2 hours Im getting hammered by ACA2689D.ipt.aol.com by Protocol TCP Length 48 for Service Radmin-port. I bet there are at least 250 connection attempts or more for this. 

Can someone tell me what Radmin-port is and more importantly, if this is something really serious? 

Wade

---

### Post by cwaldbieser on 2005-08-17
[QUOTE=wadesmart]08172005 1611 GMT-5

I have firestarter as my firewall and under Events for the last 2 hours Im getting hammered by ACA2689D.ipt.aol.com by Protocol TCP Length 48 for Service Radmin-port. I bet there are at least 250 connection attempts or more for this. 

Can someone tell me what Radmin-port is and more importantly, if this is something really serious? 

Wade[/QUOTE]
It is a port used for a Windows program called radmin (available on Win95 and up) that lets you remotely administer your computer.  It is probably not a big deal for your Ubuntu box.  If the events get annoying, just tell Firestarter to disable events on that port.  Also, under Edit -> Preferences -> Firewall -> Advanced Options -> Preferred Packet Rejection Method, make sure "Drop Silently" is checked.  Your computer will just ignore the requests without responding to them, so the antagonizers will not even know your computer exists.

It would probably be a good idea to report what you have observed to AOL, though.  Once the admins get wind of what's going on, they will probably shut down the offenders ASAP.

---

### Post by wadesmart on 2005-08-17
08172005 1913 GMT-5

Thanks for that information. Ill contact aol immediately. 

Wade

---

