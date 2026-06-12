---
title: "Unable to load network-manager-gnome"
date: 2006-09-01
forum: Networking &amp; Wireless
---

### Post by fweez on 2006-09-01
So I've installed network-manager-gnome according to the guide from the wiki but I've got a problem everytime I try to launch it..

The NetworkManager applet could not find some required resources. It cannot continue.

I even tried reinstalling it after reading some posts on the forum but still getting the same error. Any ideas?

---

### Post by fweez on 2006-09-01
Tried loading nm-applet from the terminal and this was what I got...


** (nm-applet:7907): WARNING **: Icon nm-vpn-lock missing: Icon 'nm-vpn-lock' not present in theme

(nm-applet:7907): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

---

### Post by fweez on 2006-09-01
Searched the forum based on the error message received in terminal. Solved.

Just type...

sudo gtk-update-icon-cache -f /usr/share/icons/hicolor/

in the terminal.

---

