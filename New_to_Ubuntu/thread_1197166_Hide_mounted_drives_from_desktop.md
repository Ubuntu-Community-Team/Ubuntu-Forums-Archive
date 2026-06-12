---
title: "Hide mounted drives from desktop"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by fugaki on 2009-06-25
Is there a way to not have the mounted drives show up on the desktop?

This includes samba-mounted network drives and other drives attached directly, be it the other internal drive(s) or usb drives.

---

### Post by Locutus_of_Borg on 2009-06-25
```
gconf-editor
```
navigate to Apps > Nautilus > Desktop and uncheck what you do not want visible

---

### Post by fugaki on 2009-06-25
so easy, thanks.

---

