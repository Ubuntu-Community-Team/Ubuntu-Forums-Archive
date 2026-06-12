---
title: "How to disable xscreensaver?"
date: 2011-08-06
forum: New to Ubuntu
---

### Post by WubiAR on 2011-08-06
Already did this part:
Settings > Screensaver > Mode: Disable Screen Saver.

Yet, when I open my laptop from standby, I still see the "x-screensaver" log-in screen launched with its fiery icon. How can I completely disable it?

---

### Post by Toz on 2011-08-06
Try this:
**/etc/default/acpi-support**

Change:
> LOCK_SCREEN=true
to:
```
LOCK_SCREEN=false
```

---

