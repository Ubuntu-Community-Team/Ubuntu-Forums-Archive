---
title: "FAT32 with Read/Write?"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by tsunamikitsune on 2009-05-11
I've been having a very difficult time with this, so any help would be appreciated. I created a FAT32 partition between my Windows partition and my Linux partition for the purpose of sharing my music, pictures, and other documents between the two. The only problem is, Ubuntu doesn't want me to modify files in the FAT32 partition.

It started out that I couldn't write files to it (when I tried to download files from the internet to the FAT32 partition through Firefox, for example, they would simply not download), but a bit of searching helped me fix that. I thought everything was fine until I decided to do some homework that I've been putting off, which requires me to load a document in OpenOffice from my FAT32 drive.

The document opened fine, but it's Read-Only. In fact, everything on the partition is Read-Only. I tried changing the permissions to Read-Write, but it just resets them automatically. It's getting pretty frustrating.

How can I read and write files on my FAT32 partition?

---

### Post by Didius Falco on 2009-05-11
Change the permissions on the mount point.

```
sudo chmod -r 777 /media/yourmountpoint 
```

BTW, 9.04 can read/write to NTFS just fine, so it's not a requirement to use fat32.

Regards

Didius

---

### Post by hw-tph on 2009-05-11
You need to set up a proper entry for your partition in /etc/fstab. You can specify the files and directories on this partition to be owned by your own user (by using the uid option) which would allow you to do pretty much anything you want on the drive, or set a umask to allow a group of users use it. You can read more in the mount and fstab man pages (type **man 8 mount** and **man fstab**).

Keep in mind FAT32 is not a Linux filesystem and doesn't handle permissions in a decent way. That's why we need ugly solutions like this.

Example:
```
/dev/hde1       /mnt/mypartition	vfat		user,umask=0000,iocharset=utf8   0    0
```

---

### Post by tsunamikitsune on 2009-05-11
> **hw-tph said:**
> You need to set up a proper entry for your partition in /etc/fstab. You can specify the files and directories on this partition to be owned by your own user (by using the uid option) which would allow you to do pretty much anything you want on the drive, or set a umask to allow a group of users use it. You can read more in the mount and fstab man pages (type **man 8 mount** and **man fstab**).

Keep in mind FAT32 is not a Linux filesystem and doesn't handle permissions in a decent way. That's why we need ugly solutions like this.

Example:
```
/dev/hde1       /mnt/mypartition	vfat		user,umask=0000,iocharset=utf8   0    0
```

That seemed to work. Thank you. :D

---

