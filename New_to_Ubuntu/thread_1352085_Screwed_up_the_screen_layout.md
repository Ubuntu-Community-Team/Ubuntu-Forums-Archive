---
title: "Screwed up the screen layout"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by dunbrokin on 2009-12-11
In an attempt to get rid of the notification, which I thought was causing a problem (it turns out that it was not this!) I entered the following..


sudo mv /usr/share/dbus-1/services/org.freedesktop.Notifications.service /usr/share/dbus-1/services/org.freedesktop.Notifications.service.disabled

How do I undo this as I have completely screwed up my screen layout etc...I cant even get a terminal!!

---

### Post by Greenwidth on 2009-12-11
ALT+F2 to run application > gnome-terminal

Then move it back:
sudo mv /usr/share/dbus-1/services/org.freedesktop.Notifications.service.disabled /usr/share/dbus-1/services/org.freedesktop.Notifications.service

---

### Post by dunbrokin on 2009-12-11
Thanks....you saved my a**

much obliged

---

