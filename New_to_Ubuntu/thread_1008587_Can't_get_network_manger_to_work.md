---
title: "Can't get network manger to work"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by ColinGuy on 2008-12-11
Please help out can't get network manger to work. I typed nm-applet into the terminal and I got this:> root@colin-pc:/home/colin# nm-applet
libnotify-Message: Unable to get session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)

** (nm-applet:10390): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3


(nm-applet:10390): GConf-WARNING **: Directory `/system/networking/connections' was not being monitored by GConfClient 0x9bc8078

(nm-applet:10390): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
root@colin-pc:/home/colin# 

:confused:

---

### Post by spiderbatdad on 2008-12-11
have you made any special configuration to /etc/network/interfaces?

---

### Post by albinootje on 2008-12-11
> root@colin-pc:/home/colin# nm-applet

You're trying to run nm-applet as root.
That's not handy with network-manager, and that explains also the errors.

If you want to restart network-manager in Ubuntu Intrepid you would use /etc/init.d/NetworkManager restart (I think before in earlier versions of network-manager /etc/dbus.d/ files were used, or perhaps it was in Debian)

Can you explain a bit more what is not working for you with network-manager ? 
Is wireless not working or is your wired connection through network-manager not stable ?

---

### Post by ColinGuy on 2008-12-12
I have got i working now! :popcorn::p

---

### Post by ColinGuy on 2008-12-12
Thx

---

