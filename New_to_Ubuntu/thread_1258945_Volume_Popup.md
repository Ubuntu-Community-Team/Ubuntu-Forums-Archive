---
title: "Volume Popup"
date: 2009-09-05
forum: New to Ubuntu
---

### Post by Dumbestcrayon on 2009-09-05
Is there a way to disable the volume animation from popping up in 9.04?

I have a volume bar on my Toshiba laptop and I bump it once in a while and I hate that the volume bar shows up at random times.

---

### Post by coldReactive on 2009-09-05
To disable those annoying libnotify popups:

```
sudo mv /usr/share/dbus-1/services/org.freedesktop.Notifications.service /usr/share/dbus-1/services/org.freedesktop.Notifications.service.disabled
```

To re-enable:

```
sudo mv /usr/share/dbus-1/services/org.freedesktop.Notifications.service.disabled /usr/share/dbus-1/services/org.freedesktop.Notifications.service
```

Need to restart X after you disable/enable. Also, this disables all of the libnotify popups (IE: Internet connection, etc.)

[Found here](http://enli.co.cc/ubuntu/how-to-get-rid-of-annoyances-of-ubuntu-9-04-jaunty-jackalope/)

---

### Post by Dumbestcrayon on 2009-09-05
> **coldReactive said:**
> To disable those annoying libnotify popups:

```
sudo mv /usr/share/dbus-1/services/org.freedesktop.Notifications.service /usr/share/dbus-1/services/org.freedesktop.Notifications.service.disabled
```

To re-enable:

```
sudo mv /usr/share/dbus-1/services/org.freedesktop.Notifications.service.disabled /usr/share/dbus-1/services/org.freedesktop.Notifications.service
```

Need to restart X after you disable/enable. Also, this disables all of the libnotify popups (IE: Internet connection, etc.)

[Found here](http://enli.co.cc/ubuntu/how-to-get-rid-of-annoyances-of-ubuntu-9-04-jaunty-jackalope/)


Thank you very much. Do you know if there is a way to disable only the volume indicator?

---

### Post by coldReactive on 2009-09-05
I wouldn't know, since I don't mind the popups (except when pidgin integrates with it.)

---

### Post by Dumbestcrayon on 2009-09-05
> **coldReactive said:**
> I wouldn't know, since I don't mind the popups (except when pidgin integrates with it.)

Yeah I like them but I just get tired of the volume one popping up when I bump my volume knob on my computer. lol

---

