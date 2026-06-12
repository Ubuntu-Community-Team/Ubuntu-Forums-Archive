---
title: "[SOLVED] Won't let me trash empty media file"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by selehka on 2008-12-13
Ok - now I've managed to search and find solutions for every problem I've had happen so far (except the non-working headphone situation), but can't find the solution to this one.

We use a removable media R4 - 1 G.  DL a free zip game, unpackage - all works fine.  Load the media, and now I have an empty file sitting on my desktop.  Loaded 4 games at different times, and each time the R4 media file is plugged in it makes a file, but has nothing in it.  Tried to put empty file in trash - won't let me.  Got tired of looking at them and decided to just put them in a file in my home, tried making a new file to put them in - won't let me.  Says cannot move to trash - do I want to delete.  I say yes, and nothing happens - still looking at that empty file.

These are not needed, just a nuisance eye sore.  At this rate I can see my whole desktop covered with "1.0 Gb Media" icons.  I know it's got to be something simple!  o.0

properties tells me it's a folder, it's empty and it is a file system msdos.  Permissions unknown.  Now - how can I delete them?

---

### Post by Moop on 2008-12-13
Use gksudo nautilus in a terminal to open a nautilus window with sudo permissions. Then navigate to the files you want to delete and you should be able to delete them.

---

