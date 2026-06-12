---
title: "Screen resolution"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by Willthebeeguy on 2009-07-20
Hello, my wife has changed the screen resolution on her partition to the extent that NONE it is accessible.  The resolution cannot be read by our monitor.  I can get in mine, but I can't change it from there.  Where can I go to change her resolution?

Thanks!  Will

---

### Post by komputes on 2009-07-20
Boot into recovery mode and run the xfix script this should reset the resolution to default.

 [https://wiki.ubuntu.com/RecoveryMode?action=show&redirect=BootingIntoRecoveryMode](https://wiki.ubuntu.com/RecoveryMode?action=show&redirect=BootingIntoRecoveryMode)

---

### Post by CatKiller on 2009-07-21
> **Willthebeeguy said:**
> Where can I go to change her resolution?

Per-user resolution settings are stored in ~/config/monitors.xml. Delete this file from your wife's Home folder and the resolution for her account will be reset to the default. You can either do this from the virtual console (Crtl-Alt-F1) by having your wife log in and running ```
rm ~/.config/monitors.xml
``` or graphically as root by running ```
gksudo nautilus
```

---

