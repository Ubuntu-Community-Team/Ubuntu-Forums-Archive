---
title: "Can't download photos"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by SusieQ on 2009-01-03
Hi I have a Kodak DX7630 which allows me to download photos into F-spot the first time, when I try and download again, it comes up with the following error message:-

DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)

:(

at the same time F-spot auto starts and comes up with an error message.

I've tried adding a new user and it works fine if I log in as this user, so I think something may have been corrupted in my own config. Any help very much appreciated.

Susie

---

### Post by SusieQ on 2009-01-03
I've uninstalled f-spot and the camera mounts fine, it seems f-spot claims the camera when it's plugged in then fails miserably to communicate with it. Does anyone know where the per-user f-spot config files are? Thanks

---

### Post by wmoore on 2009-01-03
> **SusieQ said:**
> I've uninstalled f-spot and the camera mounts fine, it seems f-spot claims the camera when it's plugged in then fails miserably to communicate with it. Does anyone know where the per-user f-spot config files are? ThanksI don't know a great deal about it but user config and data files are in one or both of the following locations:
```
~/.gconf/apps/f-spot
~/.gnome2/f-spot
```You could try renaming one of these folders, then running the program and see what happens.

---

### Post by SusieQ on 2009-01-03
Thank you, in the end I deleted the whole .gconf folder :) the problem seems to be that I had checked the "perform this action automatically" when asked if I wanted to open F-Spot and it didn't seem to give Gnome time to unmount the camera and hand it to F-Spot. Or something like that :)

thanks, Susie.

---

