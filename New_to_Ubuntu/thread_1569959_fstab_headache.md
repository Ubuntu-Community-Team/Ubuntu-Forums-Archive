---
title: "fstab headache"
date: 2010-09-07
forum: New to Ubuntu
---

### Post by mps69 on 2010-09-07
Yes another person with fstab problem
I'm honestly pulling my hair out with this one, and I just can't get my head round it.
Little bit of background, using Ubuntu 10.04, with 2 external drives, one with music. The second drive has to two partitions, one of these has all my movies.
I have set Rhythmbox to point towards my music drive.
When re-boot the PC the drive changes and Rhythmbox can't find the music drive.
I've tried using py-Storage Device Manager to set the drives as static, but this doesn't seem to work.
All the drive are set to mount automatically at boot up, and for the best part this works.
I've done a great deal of hunting around, and research on the subject, but i just can't understand the process fully, normally I can follow tutorials but not this time, and it's kinda embarrassing. :redface: 
I'm hope someone throws me a life line here.
i can post the fstab if that will help.

---

### Post by CharlesA on 2010-09-07
You can set it to mount drives by UUID, instead of /dev/sdxy, which is probably easier to deal with if the drive designations change.

It will look like this:

```
#RAID Array
UUID=05c730b5-680d-4d33-8e2e-76947d7a93fa       /array  ext4    noexec  0      0

```

You can use this to find out the UUID:

```
sudo blkid /dev/sdxy
```

---

### Post by Rubi1200 on 2010-09-07
This might also be useful:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

