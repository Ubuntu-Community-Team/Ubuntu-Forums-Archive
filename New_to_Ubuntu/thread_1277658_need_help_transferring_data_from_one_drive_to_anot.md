---
title: "need help transferring data from one drive to another with partimage"
date: 2009-09-28
forum: New to Ubuntu
---

### Post by thebestofall007 on 2009-09-28
i am having a problem with partimage that happens for example when you transfer a 40 gig partition onto for example a 500 gig partition where the free space only reads as large as the original partition. how do i zero out the free space on the larger partition so that the disk space reads properly and the new partition space is fully utilized?

---

### Post by LewRockwell on 2009-09-28
> **thebestofall007 said:**
> i am having a problem with partimage that happens for example when you transfer a 40 gig partition onto for example a 500 gig partition where the free space only reads as large as the original partition. how do i zero out the free space on the larger partition so that the disk space reads properly and the new partition space is fully utilized?

normally you transfer data/partition(s)/clones and then perform any desired partition/disk maintenance/administration using the software of your choice

we use Gparted(sometimes via Puppy Linux LiveCD and sometimes with PartedMagic LiveCD)

.

---

### Post by thebestofall007 on 2009-09-29
> **LewRockwell said:**
> normally you transfer data/partition(s)/clones and then perform any desired partition/disk maintenance/administration using the software of your choice

we use Gparted(sometimes via Puppy Linux LiveCD and sometimes with PartedMagic LiveCD)

.

yes, that works, but gparted is very slow (i've had it take about 8 hours)because it basically clones the partition free space and all. partimage is much faster and in my experience much more reliable because it transfers the used blocks only in a matter of minutes.

---

### Post by LewRockwell on 2009-09-29
> **thebestofall007 said:**
> yes, that works, but gparted is very slow (i've had it take about 8 hours)because it basically clones the partition free space and all. partimage is much faster and in my experience much more reliable because it transfers the used blocks only in a matter of minutes.

gparted **_*creates clones?!?!?**_*

.

---

### Post by thebestofall007 on 2009-10-01
> **LewRockwell said:**
> gparted **_*creates clones?!?!?**_*

.

well, yes. if you have two partitions where they are of equal size on the same drive for example, you can copy one partition to another, but i havent had much luck copying data from one physical drive to another because it doesnt let me, and even when transferring data from one partition to another, it is slow because it moves everything (free space and all) a certain block size at a time. that takes a long time especially if you have a lot of data. with partimage, it takes a couple of minutes because it does the work from an image, but like i explained earlier, if the partition/hard drive is larger than the partition that the image was taken from, the free space doesnt show up correctly.

---

### Post by Mark Phelps on 2009-10-01
Last time I used Partimage, it only transferred partitions intact.  There was no ability to resize as part of that operation.

Also, you said transfering a partition into another partition -- which you basically can not do.  I think what you meant is migrating a 40GB partition onto a 500GB drive.

In that case, you should be able to do the following:
1) Use Partimage to clone the partition to the larger drive
2) Use GParted to resize the cloned partition on the larger drive.

Since GParted is then not copying anything, the resize operation should not take long to perform.

---

### Post by drs305 on 2009-10-01
You use the app "resize2fs" to accomplish what you want to do. The reference link I formally used is no longer valid, but a quick search and review of the man pages will show you how to do it.


*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

---

### Post by thebestofall007 on 2009-10-21
> **Mark Phelps said:**
> Last time I used Partimage, it only transferred partitions intact.  There was no ability to resize as part of that operation.

Also, you said transfering a partition into another partition -- which you basically can not do.  I think what you meant is migrating a 40GB partition onto a 500GB drive.

In that case, you should be able to do the following:
1) Use Partimage to clone the partition to the larger drive
2) Use GParted to resize the cloned partition on the larger drive.

Since GParted is then not copying anything, the resize operation should not take long to perform.

that sounds right, and if anything comes up, i'll chime in. sorry i took so long to respond (i have a beast of a computer but dont have my own internet access).

---

