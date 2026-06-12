---
title: "Deleting files on a USB EHD"
date: 2011-05-17
forum: New to Ubuntu
---

### Post by mpjf01 on 2011-05-17
I am trying to delete several files that are on an external Hard disk formatted in EXT2. The move to trash option (and others) are greyed out when I right click on the file. Any suggestions?

---

### Post by fabricator4 on 2011-05-17
> **mpjf01 said:**
> I am trying to delete several files that are on an external Hard disk formatted in EXT2. The move to trash option (and others) are greyed out when I right click on the file. Any suggestions?

This usually means you do not have permission to do those operations on that filesystem.  One reasons for this is if you formatted the device as root and took ownership of the filesystem.  This is easy to do with the disk utility, as it's not clear when you format the device that "take ownership" actually means take ownership as root. Another reason is if you wrote the files with another login etc.

There's a few different ways around this:

Use command line and sudo to delete the files

Use "gksu nautilus" and delete the files with file manager,

Or take control of the filesystem back by making yourself owner (which also requires root privileges as per the previous two options.

If you want the nautilus file manager method press <alt><F2> and type in the box "gksu nautilus".  This will open the file manager with root privileges.  This is dangerous, do NOT mess up, and do not leave it open longer than necessary, and do not forget.  I suggest you change the background to bright red as soon as you open it to remind yourself:
Edit->Backgrounds and emblems-> then click the "colors" button then drag "fire truck red" to the background of the file manager.  Now, whenever you open file manage with root privileges it will be bright red to remind you not to mess up and to close the file manager as soon as you are finished with it.

If you need more guidance on how to delete the files or change ownership, please ask.

Chris.

---

### Post by coffeecat on 2011-05-17
Right-click on the files and look at the permissions tab under Properties. Are the files owned by root? If so, open a root file browser from the terminal with:

```
gksudo nautilus --no-desktop
```Navigate to your external drive under where it is mounted in /media and delete the files. If you simply use the delete key, they will probably only be moved into a hidden trash folder on the external drive, so if you're sure you want to delete them permanently, use the shift-delete key combination.

---

### Post by mpjf01 on 2011-05-18
The right click told me that the "permissions could not be determined". Nevertheless the remedy suggested did work so thank you both for your advice.:D

---

