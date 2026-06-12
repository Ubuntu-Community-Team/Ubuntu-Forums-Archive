---
title: "How to remove hidden junk files"
date: 2009-07-25
forum: New to Ubuntu
---

### Post by infestor on 2009-07-25
how can i remove those unnecessary files with tilde (~)? is there a command to remove 'em all?

---

### Post by infestor on 2009-07-25
also why do some files get hidden?

---

### Post by halitech on 2009-07-25
files with a ~ aren't "junk" files, they are backups so you may not want to actually remove them. If you do, try this
```
rm *~
```
be very careful where you run this command (or any that includes rm as it bypasses the trash and is very difficult to restore)

as far as why some files are hidden, usually they are configuration files or backups that are best left alone.

---

### Post by mapes12 on 2009-07-25
Not sure if this is what you're looking for but it may help:

[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

---

### Post by infestor on 2009-07-25
> **halitech said:**
> files with a ~ aren't "junk" files, they are backups so you may not want to actually remove them. If you do, try this
```
rm *~
```be very careful where you run this command (or any that includes rm as it bypasses the trash and is very difficult to restore)

as far as why some files are hidden, usually they are configuration files or backups that are best left alone.

yes i guess it is best to leave configuration files alone but for example those *.tex* files are most possibly some versions (autosave). actually i dont know why i get annoyed by those ~ed files :)

---

### Post by Barriehie on 2009-07-25
This thread might help. [Click here](http://ubuntuforums.org/showthread.php?t=814040).

Barrie

---

### Post by oldos2er on 2009-07-25
Every time you edit a file with gedit, it creates a backup file (they're not hidden). You can change this behavior in gedit via the menus Edit, Preferences, Editor, File Saving, uncheck the box next to "Create a backup copy...."

---

