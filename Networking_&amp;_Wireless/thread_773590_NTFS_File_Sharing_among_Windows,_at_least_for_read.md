---
title: "NTFS File Sharing among Windows, at least for reading..."
date: 2008-04-29
forum: Networking &amp; Wireless
---

### Post by chenzhen_li on 2008-04-29
All the forums say, you have to change the suid and then change the fstab line and blah blah, etc. Nothing happend.

I share one folder over Samba, i name it Wuajajaja in my home folder. Then, inside the folder i make a soft link like ln -s to the ntfs mounting point.

something like this ln -s /media/NTFS-DRIVE-MOUNTED ~/ntfs_for_reading_sharing_folder

then konqueror ntfs_for_reading_sharing_folder

and wualaaa, it works!!.

From Santiago, Chile, hope it works!.
:guitar:

---

