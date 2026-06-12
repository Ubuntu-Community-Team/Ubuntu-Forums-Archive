---
title: "Lost top panel"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by gotanothergrot on 2009-02-17
Help i have somehow lost my top panel showing  'system, applications etc'  and can't get it back.

---

### Post by whoop on 2009-02-17
right click existing panel. select new panel. Add items you are missing to new panel with add to panel.

---

### Post by gotanothergrot on 2009-02-17
Thank you, i'm almost there, however i don't see the non icon (system, home, applications) in the list.

---

### Post by OrangeCrate on 2009-02-17
You're looking for "Menu Bar".

---

### Post by RomeReactor on 2009-02-17
Hi. Whenever you lose either panel, or want to restore them to their defaults and don't want to add/remove launchers and applets manually, you can run this from the terminal:
```
gconftool-2 --shutdown
```

```
rm -rf ~/.gconf/apps/panel
```

```
pkill gnome-panel
```

---

### Post by gotanothergrot on 2009-02-17
Found it, Thank you very much, whoop, orangeCrate...RomeReactor

---

