---
title: "gdm not working"
date: 2011-06-28
forum: New to Ubuntu
---

### Post by CaptainJamie on 2011-06-28
Ok, I brought it on myself, I installed gnome 3 from the PPA and I have one problem. GDM has stopped working. KDM is ok though, but I'm not sure how to set it as default. 

```
$ sudo gdm
** (gdm-binary:2158): WARNING **: Failed to acquire org.gnome.DisplayManager: Connection ":1.51" is not allowed to own the service "org.gnome.DisplayManager" due to security policies in the configuration file

** (gdm-binary:2158): WARNING **: Could not acquire name; bailing out

```

---

### Post by jtarin on 2011-06-28
> WARNING **: Failed to acquire org.gnome.DisplayManager: 
Connection ":1.51" [U]is not allowed to own the service 
"org.gnome.DisplayManager" due to security policies in the configuration file[/U]


The problem will be with the dbus config
file installed by it. Look for a gdm-related file (gdm.conf?)
in "/etc/dbus-1/system.d" - it'll contain a policy section _restricting_ the
ownership of org.gnome.DisplayManager to a particular user or group, or
to at_console, or something.

---

