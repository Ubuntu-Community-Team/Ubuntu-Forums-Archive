---
title: "Thunar loses Home Directory"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by mesmith on 2009-04-15
Bit of a problem here.  Used PartImage recently, so had a backup.
Wanted to move some wallpaper into a directory in my file system.  Normal Thunar would only rubberband my drag and drop, so used a sudo thunar.  Dragged and dropped the wallpaper to the correct directory using shift/drag.  All looked fine.  X'd out of thunar and found that no menu items would load software.  Rebooted only to find that I get logon msg stating that my home directory appears not to exist.  Used PartImage to restore my system.  All is fine, but what did I do wrong???

---

### Post by boof1988 on 2009-04-15
> **mesmith said:**
> Bit of a problem here.  Used PartImage recently, so had a backup.
Wanted to move some wallpaper into a directory in my file system.  Normal Thunar would only rubberband my drag and drop, so used a sudo thunar.  Dragged and dropped the wallpaper to the correct directory using shift/drag.  All looked fine.  X'd out of thunar and found that no menu items would load software.  Rebooted only to find that I get logon msg stating that my home directory appears not to exist.  Used PartImage to restore my system.  All is fine, but what did I do wrong???

Maybe (next-time) try...
```
gksu thunar
```

-or-
```
gksudo thunar
```

instead of..
```
sudo thunar
```

See [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo).  IIRC the file permissions can get messed up when using "sudo" (instead of "gksu") for graphical applications.

---

### Post by mesmith on 2009-04-16
Thanks, I'll remember that.

---

