---
title: "[SOLVED] Gnome Applications menu killed by Main Menu editor (alacarte) part 2"
date: 2010-06-18
forum: New to Ubuntu
---

### Post by connellc on 2010-06-18
In ~/affecteduser/.config/menus, you have a list of undo files.

Take the most recent "applications.menu.undo-xxx" and paste it into another (or empty) folder. Rename it to "applications.menu" only. Paste it back into ~/affecteduser/.config/menus. It will overwrite the corrupted "applications.menu".

---

