---
title: "X11VNC stops working after long period of inactivity"
date: 2014-06-06
forum: Networking &amp; Wireless
---

### Post by Bob_Hartung on 2014-06-06
I've installed x11vnc on a couple of PCs running the most current version of Lubuntu (Ubuntu 14.04 LTS). x11vnc loads automatically on boot up using an /etc/init/x11vnc.conf file. I access it from a Windows 7 PC using UltraVNC. Everything works fine; a VNC session can be initiated when the Lubuntu PC is at the logon prompt.

However, if the Lubuntu PC is left unaccessed for a long period like several hours, either the active VNC session that was left running no longer responds or a new session cannot be initiated. The mimimum fix is to simply logout the Lubuntu PC and then it can be accessed through VNC again.

I've checked the Lubuntu PC's Task Manager and it shows that command x11vnc is running when it's in the state where it won't allow a VNC session to be initiated.

Any thoughts as to why this happens or what I can do to fix this?

Thanks.

---

### Post by jared-fernandez on 2014-06-19
I've been noticing a similar issue for quite a while now.  I am running the latest Ubuntu (14.04) and use x11vnc to access a wine process as a service.  After a period of inactivity, the wine process seems to hang and I can no longer VNC into x11vnc, but I can still see it running on the server.  The error that I get when trying to VNC is "Authentication Error" even though I am positive the password is correct.

Eventually, it seems to suddenly start working again and I am able to VNC into it (without restarting the process).  When I do this, the wine program that is running also starts to respond again.  It's almost like trying to login to x11vnc "wakes it up" and it takes a little while before it will start responding again.  I am not convinced whether or not it's possible that x11vnc could have any direct effect on a process that is running in a x11 instance, so this particular symptom (wine process responding) may be unrelated.

---

