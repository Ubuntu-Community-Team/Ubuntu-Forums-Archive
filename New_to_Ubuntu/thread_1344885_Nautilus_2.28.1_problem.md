---
title: "Nautilus 2.28.1 problem"
date: 2009-12-03
forum: New to Ubuntu
---

### Post by nutpants on 2009-12-03
i have 25 gigs in a directory on one drive
and 24 gigs in the same directory on another drive

i want to copy directory a to directory to to update it and skip all the files that are all ready there.

problem.
i have only 5 gigs free
and Nautilus 2.28.1 will not copy until the drive is filled as
"there is not 25 gigs free" 
there is only maybe 1.5 gigs different.
out of the 5000 files in the directory

how do i make Nautilus 2.28.1 just firckin copy and skip until the drive is filled? (or not filled)

nutz

---

### Post by mprince on 2009-12-03
I would think you could just press the "Skip All" button. Nautilus should still copy any files that aren't duplicate names.

If it won't for whatever reason then try using rsync to copy the files.

Open a terminal and type this:

```
rsync --ignore-existing -a /path/to/folderA/ /path/to/folderB
```


the '--ignore-existing' option will only copy the files that aren't already in folderB.

---

