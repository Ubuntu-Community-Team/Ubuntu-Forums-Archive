---
title: "KDE Network status Icon"
date: 2006-12-30
forum: Networking &amp; Wireless
---

### Post by Tanker Bob on 2006-12-30
In Gnome with Ubuntu 6.10, I had a network status icon on the task bar. Is there a way to get the same thing on the KDE task bar? I've searched the forums and the repositories but haven't found anything.  Thanks!

---

### Post by Erunno on 2006-12-30
I'm not sure if it is exactly what you are looking for but you can give knetworkmanager a try. It's a KDE frontend to network manager and installs a network status applet in the traybar. You'll have to comment out all interfaces in /etc/network/interfaces except the ones containing lo. After a restart it should work.

Cheers,
Erunno

---

### Post by Tanker Bob on 2006-12-30
Thanks!  I'll play with it and see what I can do with it.

---

### Post by Tanker Bob on 2006-12-30
Well, this doesn't do what I was seeking.  I wish to find a tray icon that flashes when data is uploaded/downloaded on the network.  This way I can monitor what's happening.  There is a plugin for Gnome, but I cannot find one for KDE.

---

