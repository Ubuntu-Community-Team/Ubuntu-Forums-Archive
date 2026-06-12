---
title: "Grsync: Can I Move file rather than Delete file on destination?"
date: 2011-04-13
forum: New to Ubuntu
---

### Post by Mike_tn on 2011-04-13
I ran Grsync sucessfully for the first time yesterday to backup a nest of folders from a USB drive to a destination location on a large external hard drive.  I used the default settings plus the extra check box for "Delete on destination."
> Delete on destination : delete files in destination which are not present in the sourceWorked very well. For larger backups an alternate option would be safer but I can't find the option I'm looking for in Grsync. A choice like "Move files in destination (not present in the source) to empty folder of same name on root of destination" would be nice. Anything like that possible, so only source files are found on the destination but also the changes are selected out and preserved somewhere rather than trashed?

---

### Post by Mike_tn on 2011-04-14
24 hours, 43 views and no reply so I assume it's not possible or not easy.

I came up with an alternate idea to try, maybe this is more typically done: Do not tick the "Delete on destination" box in Grsync. Then after running backup, compare the source and destination directories using a tool like Krusader, Gnome Commander, emelFM2 or Meld. I havn't tried any of these on directories so I will have to see which is easiest for selecting the differences out and moving them to new folders, preferably of the same folder name.

---

