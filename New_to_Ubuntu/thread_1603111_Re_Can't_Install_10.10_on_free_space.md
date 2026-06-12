---
title: "Re: Can't Install 10.10 on free space"
date: 2010-10-22
forum: New to Ubuntu
---

### Post by Peterfc on 2010-10-22
Hi i have a similar problem to a previous poster. I have just tried to install 10.10 on a 250Gb drive with one partition for windows and free space as 2.3GB. i can't figure out how to change the windows partition so i can install Ubuntu.

I got to this post by doing a search for Partitions but was advised to create a new Post.

I have included a screen shot.

I have my drive at

Sda1 201.7GB
Free space 2277MB

---

### Post by 3rdalbum on 2010-10-22
Firstly, that's not enough free space for Ubuntu. You need to resize the Windows one downward. The bare minimum space required for Ubuntu is 2.3 GiB if I remember correctly, but most people here would recommend around 10 GiB.

Once you've done that, click on the "Free Space" and click Edit. This opens up a new window where you can specify a filesystem type (choose "ext3" or "ext4") and what the "mount point" of the partition should be; this should be simply a slash:

```
/
```

The slash just means "the root file system".

Unfortunately you've done things the difficult way. The Ubuntu installer can make it very easy to create your partitioning, provided you HAVEN'T provided the unpartitioned space to begin with.

---

### Post by ArgusVision on 2010-10-22
Ok. Yes you need to resize your windows drive. Check a couple of things first. 
Boot into Windows.
In XP, right click "My Computer" and select "Manage". Then, select "Disk Management". 
In Vista, click Start. Right Click "Computer" and select "Manage". Then, select "Disk Management".


 - How much of the Windows drive (usually C) is used up by actual files/data? You may need to move some files to a removable drive to make room.
- Run a defragment, to keep from accidentally overwriting any stray files.

Next, you can boot into your Ubuntu live CD. 
You should be able to continue to edit your partitions.

---

### Post by ArgusVision on 2010-10-22
Well, I guess from the pictures I didn't need to explain to you how to ge to disk management...

---

