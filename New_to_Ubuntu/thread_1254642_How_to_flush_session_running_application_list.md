---
title: "How to flush session running application list"
date: 2009-08-31
forum: New to Ubuntu
---

### Post by Sapfeer on 2009-08-31
Hi!

Some days ago I checked on "Automatically remember running applications when logging out" in System -> Preferences -> Startup applications and then checked it off, but Ubuntu had remembered some applications which I don't want to start after boot now... How can I make it out?..

---

### Post by Uzi304 on 2009-08-31
System->Preferences->Startup Applications. Uncheck anything you don't want to start on startup.

---

### Post by Sapfeer on 2009-09-01
> **Uzi304 said:**
> System->Preferences->Startup Applications. Uncheck anything you don't want to start on startup.
Thanks for you answer, but your solution is not good for me, because session configuration is stored in another place than startup application. I've done my problem just issuing the following:
```
rm ~/.config/gnome-session/saved-session/*
```

---

