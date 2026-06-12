---
title: "FAT32/External HD/Permissions/Read-Only HELP!"
date: 2010-08-01
forum: New to Ubuntu
---

### Post by Lesss on 2010-08-01
So I managed to get my HD formatted with FAT32 so its compatible with my PS3...my problem now is that its telling me that its read-only and will not let me download/move/create anything in my HD.

This is a problem because the whole reason I got the Hd was to watch things on my PS3 and for storage.

Can someone please tell me how to fix this!!

I tried changing permissions and it won't let me....

---

### Post by jtarin on 2010-08-01
> I tried changing permissions and it won't let me....
What method did you use? Have you tried mounting the partition and how?
Try this example:```
sudo mkdir /media/FAT32
sudo mount /dev/sdaX /media/FAT32
sudo chmod 777 /media/FAT32
```
What is happening is that /media/FAT32 represents different directories before and after the mount. Before it's the directory you made, and which you chmod'ed 777. After, it's the root directory of the filesystem in /dev/sdaX.

**_Post your /etc/fstab_**

---

