---
title: "ext3 storage partition, permission denied...please help"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by Yellowpolkadot1040 on 2009-04-07
i recently installed ubuntu on my samsung nc10. While doing so, I created 3 partitions...one 30gb partition for xp, one 35gb ext3 partition for ubuntu, and a 90gb ext3 partition for storage. The problem lies with the storage drive...When i try to move files over to the drive (after it has been mounted, of course), or any folder within the drive, i get an error message that reads "Error while copying "background image.jpg".There was an error copying the file into /media/disk." and "Error opening file '/media/disk/background image.jpg': Permission denied".

I have tried going in and changing the permissions of the drive, and when I right click and open preferences, then click on the permissions tab, It reads "the permissions of "disk" could not be determined". 

I am thinking that the permissions belong to root?? but don't know how to check that, or change the permissions so that I have full read/write capabilities. I am thinking that there might be a way to do it in terminal? 

I would really appreciate any help, or additional info any of you could supply. 

Please be as simple, and descriptive as possible, I'm pretty new to linux and ubuntu (coming from the mac world) and have a limited knowledge of terminology...Thank you :)

---

### Post by taurus on 2009-04-07
Just change the ownership of the mount point for that drive from root to your login name so you can write to it anytime you want.

Assuming your login name is yellow, do

```
sudo chown -R yellow:yellow /media/disk
ls -la /media
```

p.s.  If **background image.jpg** is the name of the file, you need to include it in quotes, "background image.jpg".

---

### Post by egalvan on 2009-04-07
How was the "storage drive" formatted?

Windows-type such as NTFS or FAT32?

Linux-type such as ext2 or ext3 or reiser?


Linux is not generally capable of determining permissions of Windows-type file system,
and FAT32 basically has no permissions to set.

---

### Post by Yellowpolkadot1040 on 2009-04-07
> **taurus said:**
> Just change the ownership of the mount point for that drive from root to your login name so you can write to it anytime you want.

Assuming your login name is yellow, do

```
sudo chown -R yellow:yellow /media/disk
ls -la /media
```

p.s.  If **background image.jpg** is the name of the file, you need to include it in quotes, "background image.jpg".


Awesome...it worked!!! I figured it was a pretty easy fix...Thank you so much!!!

---

