---
title: "krdc stuck on full screen mode?"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by macrowiz49 on 2009-02-11
This problem is irritating the crap out of me, and I've tried googling everywhere for the solution with no avail.  Every time I open krdc, it goes to fullscreen mode, and I can't seem to get it into a window mode.  I tried all the toolbars, but the "fullscreen" mode is grayed out.  Is there a key-combination that I need to press?  Or is it a problem with the software, that I need to reinstall it?  I'm using it under GNOME b/c it seems to be the only VNC client that is letting me to connect to this specific computer.

---

### Post by racmar on 2009-02-16
I've just suffered this too.  The solution for me was to delete the krdcrc file.

```
mv ~/.kde/share/config/krdcrc ~/.kde/share/config/krdcrc.old
```

then restart krdc


EDIT:
This does not seem to be persistent.  If you maximize the window and close and reopen it, the same problem will manifest.  I'm guessing this has something to do w/ the update last week.

---

### Post by macrowiz49 on 2009-02-16
Thanks, that worked for now.  I'll try to remember not to maximize it for the time being.

---

### Post by prkos on 2009-02-17
In similar threads with the same problem in other applications a solution was suggested if you use Compiz [http://ubuntuforums.org/showthread.php?p=6751385#post6751385](http://ubuntuforums.org/showthread.php?p=6751385#post6751385)

---

### Post by racmar on 2009-02-18
prkos,

Thanks!  That worked for me.

---

