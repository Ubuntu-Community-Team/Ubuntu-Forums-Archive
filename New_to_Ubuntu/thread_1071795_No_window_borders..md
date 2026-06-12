---
title: "No window borders."
date: 2009-02-16
forum: New to Ubuntu
---

### Post by ____ on 2009-02-16
I dual booted ubuntu with vista and used emerald theme manager for a window border theme. I wanted to get rid of my emerald theme to use metacity, so i just uninstalled emerald and now i have no wondow borders.

---

### Post by RomeReactor on 2009-02-16
Hi. Is Compiz still active? If so, open compizconfig-settings-manager ('System->Preferences->CompizConfig Settings Manager'), scroll down and select 'Window Decoration', and make sure the command entry reads **/usr/bin/compiz-decorator**.

If you don't have CompizConfig Settings Manager:
```
sudo aptitude install compizconfig-settings-manager
```

If Compiz is not running, press ALT+F2 and run:
```
metacity --replace
```

---

### Post by supersonicdarky on 2009-02-16
if you have to do this every time it you log on, then just add **metacity** to your sessions.

---

### Post by ____ on 2009-02-16
Thanks it worked.:D

---

