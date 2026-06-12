---
title: "Disable Notification Pop-Ups"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by dmillerct on 2009-11-16
I am trying to disable the notification pop ups you see when you navigate over an object in gnome. I have gone to the gconf-editor and navigated to apps, panel, global and un-checked the option tool tips_enabled. However when I hover over an item in the notification area or in the window selector section of the panel they still show up. (see screen shot)

---

### Post by coldReactive on 2009-11-16
> **dmillerct said:**
> I am trying to disable the notification pop ups you see when you navigate over an object in gnome. I have gone to the gconf-editor and navigated to apps, panel, global and un-checked the option tool tips_enabled. However when I hover over an item in the notification area or in the window selector section of the panel they still show up. (see screen shot)

Those are tooltips, not notifications.

> edit ~/.gtkrc-2.0
and add the line

gtk-enable-tooltips = 0

---

### Post by dmillerct on 2009-11-16
> **coldReactive said:**
> Those are tooltips, not notifications.

That did it. Thanks a heap man.

---

