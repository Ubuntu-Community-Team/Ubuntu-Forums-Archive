---
title: "My theme changes on its own"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by Adali on 2009-01-15
Hi, I'm having trouble with my desktop theme changing without me actually changing it myself. I get an error message when I try to change it back to the previous theme I had:
(Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.
If I logout then login it goes back to how I had It prior to the problem. I want to fix this issue please help.

---

### Post by mjheagle8 on 2009-01-15
can you launch gnome-settings-daemon in the terminal once it has crashed?

---

### Post by Adali on 2009-01-15
yes It seems like I can run 'gnome-settings-daemon'. But the theme is still the same...whats next???

---

### Post by mjheagle8 on 2009-01-15
is there anything returned in the terminal when you launch it? try and launch it in the terminal, then change the theme again.

---

### Post by Adali on 2009-01-15
No output from 'gnome-settings-daemon run'. But I did try to change the theme again and now it changed back to my original theme. Thanks mjheagle8.
One more question before close this thread is there a way to fix and/or prevent this crash from happening again?

---

### Post by mjheagle8 on 2009-01-15
can you look at your logs and see if there is any error occuring witht the gnome-settings-daemon to make it crash in the first place?

---

### Post by Adali on 2009-01-15
> **mjheagle8 said:**
> can you look at your logs and see if there is any error occuring witht the gnome-settings-daemon to make it crash in the first place?
where would those logs be located on my hard-drive?

---

### Post by mjheagle8 on 2009-01-15
you can view logs by going to system>administration>system log

---

### Post by Adali on 2009-01-15
Jan 15 20:15:57 adali-gateway-laptop gdm[5700]: gnome-keyring-daemon: couldn't lookup keyring component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified

---

### Post by mjheagle8 on 2009-01-15
> **Adali said:**
> Jan 15 20:15:57 adali-gateway-laptop gdm[5700]: gnome-keyring-daemon: couldn't lookup keyring component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified

this looks like its a problem with the gnome-keyring-daemon, idk if its related to the gnome-settings-daemon.

---

### Post by Adali on 2009-01-15
Thats alright. Thanks again for the info and your help.
...
...:P

---

### Post by mjheagle8 on 2009-01-15
no prob, any time :)

---

