---
title: "lost icons..."
date: 2009-07-16
forum: New to Ubuntu
---

### Post by NOTAGEEK on 2009-07-16
i accidentally deleted too many icons from the panel on top a little left of my time/date...

i removed the icon showing my internet connection and the one that showed rhythmbox there when i am using it...

is there a way to get these back ???

thanks...

---

### Post by Sub101 on 2009-07-16
The network manger can be restarted with

```
nm-applet
```

by typing it in Alt-F2

---

### Post by NOTAGEEK on 2009-07-16
> **Sub101 said:**
> The network manger can be restarted with

```
nm-applet
```by typing it in Alt-F2



nm-applet

** (nm-applet:7026): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3

---

### Post by Mornedhel on 2009-07-16
You removed the notification-area applet, which contains status icons for many applications, among which NetworkManager and probably Rhythmbox as well. Right-click on your panel, click Add To Panel, Notification Area.

---

### Post by NOTAGEEK on 2009-07-16
> **Mornedhel said:**
> You removed the notification-area applet, which contains status icons for many applications, among which NetworkManager and probably Rhythmbox as well. Right-click on your panel, click Add To Panel, Notification Area.


beeeeeutiful... solved... thanks...

:guitar:

---

