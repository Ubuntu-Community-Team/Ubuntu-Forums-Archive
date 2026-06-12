---
title: "copying files from one external HDD to another"
date: 2009-06-08
forum: New to Ubuntu
---

### Post by bjaz on 2009-06-08
hello all
I have these two external USB HDD drives, and i'm trying to move files from one to another. but they don't seem to be writeable. i can browse files, but can't create folders or actually paste files one neither of the drives.

how do i change this and make the drives writeable in XUBUNTU 
one is in FAT32 format, the other is in NTFS.

i've been reading up on the subject but am totally list in command lines or how to use them.
i must say i'm a little surprised that answers to basic questions such as this are not easy to find for people like me who are used to graphic environments. i'm guessing it's to do with permissions and the like, but i can't find a way to manage the drives like i would on mac os or windows, ie create folders, erase them, copy and paste, rename.

thanks in advance for your help

ben

---

### Post by handydan918 on 2009-06-08
Try ```
gksudo nautilus
```

That will give you a gui file manager with root permissions. You can then change permissions to your hearts content. 


Be careful.

):P

---

### Post by logos34 on 2009-06-08
but the system is supposed to automount usb (fat32 or ntfs or whatnot) at '/media/disk' with read+write access/permissions/ownership 

[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

---

### Post by bjaz on 2009-06-08
> **handydan918 said:**
> Try ```
gksudo nautilus
```That will give you a gui file manager with root permissions. You can then change permissions to your hearts content. 


Be careful.

):P

thanks.
i think it's due to the fact that the partition i'm trying to copy files to is in ntfs.
it seems i can only access it as read only.
i'm installing ntfs config to see if this will change things

edit, still stuck, can't write on this beautiful 700 gig ntfs partition...

---

### Post by logos34 on 2009-06-08
follow the steps in the link I gave to manually mount it with write access (ntfs-3g)

---

