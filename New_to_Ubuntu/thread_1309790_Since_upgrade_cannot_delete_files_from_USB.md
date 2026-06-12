---
title: "Since upgrade cannot delete files from USB"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by Sneo on 2009-11-01
Hey, recently upgraded to Ubuntu 9.10 , using KDE. However now whenever I plugin my usb drive I can't delete anything off it or copy anything over. I think this problem is there because it is FAT formatted. The options come up to delete in Dolphin but they are greyed out.

Any solutions will really be appreciated!

---

### Post by yeats on 2009-11-01
> Hey, recently upgraded to Ubuntu 9.10 , using KDE. However now whenever I plugin my usb drive I can't delete anything off it or copy anything over. I think this problem is there because it is FAT formatted. The options come up to delete in Dolphin but they are greyed out.


Actually, this sounds like a permissions issue to me...  Can you right click on one of the files you're trying to delete and select Properties, then click the Permissions tab?  It will show you the file owner and the permissions attached to it.

---

### Post by Sneo on 2009-11-01
Here are my permissions, don't know if they are right or how to change them!

---

### Post by yeats on 2009-11-01
Okay, I can see that the user is "sean" (assuming that's you :-) ), but that the group is set to "root", which is almost certainly the problem.  You should be able to run Dolphin as root by typing Alt-F2 and entering "kdesudo dolphin" (no quotes).  Then you should have the permissions to change the permissions on the USB drive's files (or just delete them from there).

---

### Post by Sneo on 2009-11-01
> **chrissharp123 said:**
> Okay, I can see that the user is "sean" (assuming that's you :-) ), but that the group is set to "root", which is almost certainly the problem.  You should be able to run Dolphin as root by typing Alt-F2 and entering "kdesudo dolphin" (no quotes).  Then you should have the permissions to change the permissions on the USB drive's files (or just delete them from there).

Still being told I cannot change the permissions. Changing permissions failed. Any other way to change the permissions of it?

[B]Update: It seems root is not allowed to change the permissions.
Maybe its the strange name on mount? /media/TG0 [symbols that cant be entered in post]

How can I change the name for it?[/B]

_Solved Sorta_
**I reformated the flash drive as FAT 32 and renamed the label to FLASH. This seems to have worked aswell as using the lvm tag in gparted**

---

