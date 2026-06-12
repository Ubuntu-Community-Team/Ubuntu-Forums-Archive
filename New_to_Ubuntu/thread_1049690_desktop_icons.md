---
title: "desktop icons"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by squrl on 2009-01-24
Is there a way to get rid of the icons on the desktop and just have text to identify the files?

Thyanks

---

### Post by squrl on 2009-01-24
Bump.

Please ??

---

### Post by blackened on 2009-01-24
You could set each icon to a blank image, but this won't be a global change and you'll have to do it to each new icon you add to the desktop.

Other than that, I don't think what you're asking is possible in Gnome.

---

### Post by spcwingo on 2009-01-24
Try opening up the file in your text editor and deleting the line marked (it'll end with .desktop):

```
Icon=somefile.png
```

Of course make a backup first.  This is the way that I have added icons on non-Gnome installs.  It should also work to remove icons on standard Gnome installs, too.

---

