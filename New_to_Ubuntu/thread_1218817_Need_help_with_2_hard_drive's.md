---
title: "Need help with 2 hard drive's"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by JoeNZ on 2009-07-21
Hello from NZ,

On my system I have an 80gb hdd (which houses Xubuntu) and a 20gb hdd which is used for extra storage.
Recently I had a go at changing the 20gb from ext3 to ext4. Now I cannot see the 20gb hdd. If I open up the Partition Editor, I can see both hdd's and it also states that the 20gb has been changed to ext4 but I cannot see it in the system normal.

Please, I need help with a few matters:


[LIST=1]
[*]How can I get the system to see the 20gb hdd?
[*]How can I add the 20gb hdd to fstab so it boots/mounts with the system on startup?
[*]How can I change the 80gb hdd - the main system hdd - to ext4, not lose anything and keep it as the main hdd?
[/LIST]
Any help would be much appreciated.

Kind regards
JoeNZ

---

### Post by Paddy Landau on 2009-07-21
What version of Xubuntu do you have?
How did you reformat the 20Gb drive?
Have you considered changing the 20Gb back to ext3?

I've read that ext4 still has some bugs, and that you should consider it unreliable until 9.10 is released.

---

### Post by superprash2003 on 2009-07-21
post output of **sudo fdisk -l**

---

### Post by JoeNZ on 2009-07-21
Xubuntu 9.04 Jaunty
I followed (not very well obviously) this guide to reformat the 20gb hdd:

[http://maketecheasier.com/how-to-upgrade-from-ext3-to-ext4-without-formatting-the-hard-disk/2009/04/21](http://maketecheasier.com/how-to-upgrade-from-ext3-to-ext4-without-formatting-the-hard-disk/2009/04/21)

If I change it back to ext3, will my system see it again?

---

### Post by JoeNZ on 2009-07-21
sudo fdisk -l reveals:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa6963dd2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9355    75144006   83  Linux
/dev/sda2            9356        9729     3004155    5  Extended
/dev/sda5            9356        9729     3004123+  82  Linux swap / Solaris

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e169d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2434    19551073+  83  Linux

---

### Post by p0cky84 on 2009-07-21
What do you mean by "see" the partition?

Do you mean that its mounted by "Seeing" it?

---

### Post by JoeNZ on 2009-07-21
I cannot see the drive anywhere in the file manager/side panel. In Ubuntu, I could see it when I was in the file manager in the side panel. When I wanted to access it, I would just click on it and the system would auto-mount it and away I went.
Once I can see it again, I was wanting to set it up so it would be visible and mounted when the system started up.

---

### Post by Fungyo on 2009-07-21
to have it auto mount at boot.
first issue this command
```
ls -l /dev/disk/by-uuid
```

make a mount point
```
sudo mkdir /mnt/mountpointname
```

than add to your /etc/fstab
```
UUID=your uuid result here /mnt/mountpointname ext4 defaults 0 1
```

---

### Post by p0cky84 on 2009-07-21
@Fungyo
DAMN YA BEAT ME!

---

### Post by JoeNZ on 2009-07-21
Thanks Fungyo. I can access it and it boots with the system. All your help was much appreciated. Thanks.

---

### Post by JoeNZ on 2009-07-21
This however has brought about another problem. I am not the 'owner' of it and cannot read and write to it. Please see attached screenshot.

---

### Post by Fungyo on 2009-07-21
Sorry for the late reply.

try this
```
sudo chown yourusername:yourgroupname /mnt/mountpoint/
```

your groupname will be your username in ubuntu

glad the first part worked

---

### Post by JoeNZ on 2009-07-21
Likewise with the late reply, just got up.

Just did it and bingo, all done. Thank you so much. Consider this solved.

---

### Post by Fungyo on 2009-07-21
no worries, happy to help :)

---

