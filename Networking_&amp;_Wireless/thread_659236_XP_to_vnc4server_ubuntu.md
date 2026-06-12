---
title: "XP to vnc4server ubuntu"
date: 2008-01-05
forum: Networking &amp; Wireless
---

### Post by iancvt55 on 2008-01-05
Hi

I'm probably trying to run before I can walk but having got my ubuntu to wireless to my network this morning I'm up for it.

Problem is from my XP machine I can vnc to the Ubuntu machine but the connection keeps getting rejected. If I ping the Ubuntu machine i get a response

Any suggestions on why the vnc is failing would be welcome.

Thanks

Ian

---

### Post by samosamo on 2008-01-06
Do you just type in the hostname of the box?  Try it with the port.  In this fashion:

```
hostname::port
```

I assume 5901 is the port so it would look like this: ubuntu::5901

---

### Post by poiiop on 2008-01-09
To use Ubuntus build in Remote Server (System, Preference, Remote Desktop), you have to log on the system first, before your XP can connect.

I you want to connect - without logging on your Ubuntu first - you can install VNC4SERVER instead. 

There are many install VNC4SERVER how to on the net - just installed it myself .. :)

---

### Post by poiiop on 2008-01-09
If VNC4SERVER allready is running ....

In a term, try typing vncserver (maybe you will be asked for a password) - finaly this should give you an answer something like lisning on localhost:1 (or localhost:2 etc) 

Then type in a term, still on your Ubuntu vncviewer localhost:1 (1 = the number that shows after typing vncserver.)

If you get an answer, you maybe just see a gray x-term windows. You can type gnome-session to load your GUI, or place the ghome-session in this file /root/.vnc/xstartup for GUI autostart.

---

