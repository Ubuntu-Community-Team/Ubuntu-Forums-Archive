---
title: "Desktop Launcher for shut down"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by mattbutsko on 2009-02-23
I need to make a desktop icon for shutting down the computer without the use of the sudo command. I've really been modding gnome to make my computer look good, and this is one of the last mods I intend on doing for a while. 

Can anyone help me out?

---

### Post by ibuclaw on 2009-02-23
Yes, you can do this. If you read the DBUS specification on the freedesktop.org site, you'll see the hook that is implemented: [http://people.freedesktop.org/~david/hal-spec/hal-spec.html#interface-device-systempower](http://people.freedesktop.org/~david/hal-spec/hal-spec.html#interface-device-systempower)

But, in short, putting this in the command box of a new Desktop Launcher /should/ shutdown your computer without asking :D

```
dbus-send --system --print-reply --dest=org.freedesktop.Hal /org/freedesktop/Hal/devices/computer org.freedesktop.Hal.Device.SystemPowerManagement.Shutdown
```

Regards
Iain

---

### Post by mattbutsko on 2009-02-23
Thanks a lot. Works great. Desktop's complete now.

---

### Post by Jingle on 2009-03-02
Show us some pics of your desktop then :P

---

