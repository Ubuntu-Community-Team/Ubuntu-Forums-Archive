---
title: "nm-applet trouble"
date: 2008-11-19
forum: Networking &amp; Wireless
---

### Post by mistervinnie on 2008-11-19
Hi,

I've been searching for a week :( now and I can't find why my nm-applet only starts when I'm in range of my already configured wireless networks (I enter the keyring password and it automatically connects)

So when I'm not at home, I can't have internet!

I just updated to Xubuntu 8.10, but I think the reason for the troubles are the system-lockups I got when trying to connect 'mobile internet' through my phone.

When I try to start nm-applet in a Terminal window I get this error message:

[INDENT]root@vincent-laptop:/home/vincent# nm-applet
libnotify-Message: Unable to get session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
GConf Fout: Niet gelukt contact te leggen met de configuratie-server; een van de mogelijke redenen is dat u TCP/IP netwerken voor ORBit moet aanzetten, of er zijn verouderde NFS locks door een systeem crash. Bekijk [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) voor informatie. (Details -  1: Verbinding maken met de sessie is mislukt: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)

** (nm-applet:6881): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3


(nm-applet:6881): GConf-WARNING **: Directory `/system/networking/connections' was not being monitored by GConfClient 0x84f0e80

(nm-applet:6881): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed[/INDENT]
 
:confused:

I've tried searching for nfslock (but according to my system that service doesn't exist), tried altering networkusersettings configuration files, but I haven't found the right solution

I hope to find some help here!

---

