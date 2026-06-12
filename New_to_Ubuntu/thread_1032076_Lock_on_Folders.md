---
title: "Lock on Folders"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by rustom on 2009-01-06
hello,

After placing files from my usb drive on to my Ubuntu desktop I noticed a lock appeared on a few of the folders. The lock symbol appeared on a file that contains music, also on a file containing pictures. I can play the music and view all the pictures but i am not able to move the files off the desktop or delete them. Any info on why the lock appeared and what i can do to get rid of it, so I can delete some items in the folders as well i would like to move them to a different location.

---

### Post by jerome1232 on 2009-01-06
Check out the permissions, they are either not owned by your or they are read only.

right click the folder, click properties, click the Permissions tab.

If it's read only make it read/write for owner and group, if they are owned by another user (you used a root nautilus to copy them???) then you will need to chown the folder.

```
sudo chown -R $USER:$USER ~/Desktop/foldername
```

---

### Post by realmoonstruck on 2009-01-06
go to the properties menu of the file/folder
select permissions
in the "Access:" field under owner change the **Read-only** to **Read and write**

---

