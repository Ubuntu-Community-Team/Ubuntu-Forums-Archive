---
title: "Creating a Thin Client"
date: 2008-07-01
forum: Networking &amp; Wireless
---

### Post by mohenjo on 2008-07-01
I'm looking to set up an ubuntu machine in such a way that it will boot up and then connect via RDP to a Windows Terminal Server (the user will enter his/her own credentials into the login screen).

Is there an easy way to tell ubuntu to skip the local login screen and instead connect to a terminal server?

---

### Post by pytheas22 on 2008-07-01
If you go to System>Administration>Login Window, you can make "secure remote connection" the default session.  I don't know if that means RDP or something else though, and I don't know how to configure it any further.  But if you play with it, maybe you can get what you need.  Don't be surprised if you can't configure everything through the GUI, however.

---

