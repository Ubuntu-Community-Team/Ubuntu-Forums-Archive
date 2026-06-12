---
title: "GUI Tool to Locate File types by size"
date: 2009-08-19
forum: New to Ubuntu
---

### Post by kendoori on 2009-08-19
I need to find a delete 0 byte files. Tracker doesn't appear to allow for filtering by file size. Is there a GUI tool available for this?

If not, can someone give me the command line syntax to locate and delete 0 byte files?

---

### Post by kanikilu on 2009-08-19
It looks like this GUI frontend to Find can search by size:

[http://www.kbrandt.com/2008/06/pygnomefind-gui-frontend-to-gnu-find.html](http://www.kbrandt.com/2008/06/pygnomefind-gui-frontend-to-gnu-find.html)

I don't see any pre-built packages for it, so you'll need to compile from source.

As for the command, I'm no expert on find, but I think the following will display 0 byte files starting from the current directory:

```
find . -size 0 -print
```

I imagine you could replace the **print** with an **-exec rm -r {} \;**, but be very careful and use print first to see what it finds...

---

### Post by kendoori on 2009-08-22
Took a bunch of searching, but this did the trick

[http://pcmanfm.sourceforge.net/](http://pcmanfm.sourceforge.net/)

The search gui worked very fast, but it didn't allow for deleting from the results list. I had previously installed Dolphin for some reason, and that worked like a charm, including being able to delete the results.

[http://packages.ubuntu.com/jaunty/kde/dolphin](http://packages.ubuntu.com/jaunty/kde/dolphin)

---

