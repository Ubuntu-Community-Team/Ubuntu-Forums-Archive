---
title: "Remote desktop on Ubuntu server"
date: 2010-02-21
forum: New to Ubuntu
---

### Post by athlon007 on 2010-02-21
hi everyone,
i have just installed ubuntu server, never used linux before.
id like to connect to ubuntu machine  from wxp machine via remote desktop, but unfortunately theres no remote desktop icon in system menu in ubuntu :confused: therefore im not able to configure remote desktop on ubuntu machine.
i have tightvnc on wxp machine.
can anybody help pls....?
thanx a lot

---

### Post by bodhi.zazen on 2010-02-21
The server edition is command line only. Did you install Gnome ?

I highly suggest you manage your server via ssh or if you need a graphical interface something like webmin.

99.99 % of managing a server involved either editing text files or running commands on the command line and gnome does nor really add much.

VNC will be slow and is insecure.

[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

If you *must* but installing gnome desktop + VNC is less then ideal for the reasons I stated.

---

### Post by stevanbt on 2010-02-21
Agreed a server should be command line - no need for a GUI.  Also agree that VNC is insecure.  However, if a remote GUI connection is required to the server then look at NX ([https://help.ubuntu.com/community/FreeNX]("https://help.ubuntu.com/community/FreeNX"))

Thanks, Steve.

---

### Post by athlon007 on 2010-02-23
thank you guys a lot for your help. im going to try to install all the required stuff. :rolleyes:

---

