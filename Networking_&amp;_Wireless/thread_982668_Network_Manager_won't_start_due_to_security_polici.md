---
title: "Network Manager won't start due to security policies"
date: 2008-11-14
forum: Networking &amp; Wireless
---

### Post by mabtjie on 2008-11-14
Hi,

I've recently been trying to install Network Manager according to the instructions at [https://help.ubuntu.com/community/WifiDocs/WPAHowTo]("https://help.ubuntu.com/community/WifiDocs/WPAHowTo").

The icon doesn't appear, so as per the instructions I run and get:

```
$ nm-applet

(nm-applet:5764): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(nm-applet:5764): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(nm-applet:5764): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(nm-applet:5764): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(nm-applet:5764): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(nm-applet:5764): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(nm-applet:5764): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

** (nm-applet:5764): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service.
  Message: 'Connection ":1.17" is not allowed to own the service "org.freedesktop.NetworkManagerUserSettings" due to security policies in the configuration file'


(nm-applet:5764): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
```

I'm on Intrepid.  According to [http://mail.gnome.org/archives/networkmanager-list/2006-March/msg00175.html]("http://mail.gnome.org/archives/networkmanager-list/2006-March/msg00175.html"), I need to setup permissions properly for this to work.

What should I be looking at to find out what the permissions actually need to be, etc.?

Thanks,
- Mab

---

### Post by iponeverything on 2008-11-15
The howto you ref'ed was for ver. 6.x

Why don't you remove/purge/reinstall network manager with dpkg.

If you don't want to do that dig around a bit in:

System -> Administration -> Authorizations

---

