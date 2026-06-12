---
title: "HUBackup (Restore ?)"
date: 2009-08-21
forum: New to Ubuntu
---

### Post by eunix1 on 2009-08-21
Before installing 9.04 I backed up my home directory (8.04 Home Backup and Restore) on my laptop.  I have the DVD with the "*.dar" file but cannot open it in a GUI as it requires root permission.  I cannot find a program with which to open the file.  I notice that HUBackup is no-longer listed in the archive.
Checked HUBackup (Solved) thread but found no solution.
Any help would be appreciated.
David

---

### Post by starcraft.man on 2009-08-21
Did some quick research, apparently the program is experimental and doesn't appear to have large dev team behind it. It was removed it seems because the restore functionality wasn't working right (figures eh?).

The better news (or worse depending) is that the backup is just a dar file, and that itself is simply an archive file like tar (dar is actually developed as replacement to tar, it supports file splitting and some other functions). A few options then present themselves:

1) Install dar to get to most options, open a terminal ad do following (or see sig on installation):

```
sudo apt-get install dar dar-docs
```

2) Learn to use dar and manipulate the archive from a terminal. For example, dar offers tutorials like this one: [http://dar.linux.free.fr/doc/Tutorial.html](http://dar.linux.free.fr/doc/Tutorial.html) . Google for more, I don't know any off hand.
2b) Supplement learning with their official documentation:
```
man dar
```
or
```
dar --help
``` 
for condensed version with options.

3) I believe, but am not certain, that if ya install dar you'll be able to use the archive mounter gui option in nautilus to mount and extract whatever files ya like from it. To do this, after step 1, navigate to file in question in nautilus and then right click > Open with archive Mounter (don't confuse with manager).

The last option has advantage of being gui. I don't use dar so can't instruct ya on it's use.

---

### Post by eunix1 on 2009-08-21
Thanks Starcraft, I will give that a try.  Will have to use a terminal though as Nautilus won't do it.  Thanks again.
David

---

### Post by starcraft.man on 2009-08-21
> **eunix1 said:**
> Thanks Starcraft, I will give that a try.  Will have to use a terminal though as Nautilus won't do it.  Thanks again.
David

No worries, if ya have questions about certain commands reply here and I'll try and help. I don't think its that different from tar. Do remember, you'll have to manually tell it where to extract all the files. If ya made a backup of all root, you'll have to do it from a live CD and tell it to extract over the existing root once mounted.

---

### Post by eunix1 on 2009-08-21
In the DAR documentation I found a link to [http://dargui.sourceforge.net/](http://dargui.sourceforge.net/) which provides a simple solution to the whole problem.  Thanks to Malcolm Poole the restore was rapid and completely painless.  Only for i386 though.
David

---

