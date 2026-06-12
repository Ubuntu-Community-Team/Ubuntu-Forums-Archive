---
title: "Shrinking Windows partition (9.04)"
date: 2009-08-06
forum: New to Ubuntu
---

### Post by ZaM0 on 2009-08-06
My previous topic with some info of what I did: [http://ubuntuforums.org/showthread.php?t=1233010](http://ubuntuforums.org/showthread.php?t=1233010)

Ok, I think I will take this step of a true installation of Ubuntu on its native file system. I have two partitions, recognized in Windows as C:/ (88GB) and D:/ (98GB). I want to shrink the D:/ drive by ~10 GB (will I need more?) and use the free space to install Ubuntu on. 

So I shrink the volume using the Computer Management in Vista and the shrinked space will be unallocated, right? And when I point that unallocated space Ubuntu will handle the rest? Simple as that?

Oh and I've read few posts, someone was saying his hard disk failed after an Ubuntu installation, this is because of a pre-damaged hard drive, isn't it? I've done a recent chkdsk /r and no bad sectors were found, so all should be safe?

---

### Post by jmszr on 2009-08-06
ZaMO,

This guide discusses standard dual-boot installation starting at the bottom of page 9:  [http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html) . (free .pdf download)

Be sure and defragment your D:\ partition a couple of times first. You can shrink the D:\ partion from within Windows if you choose to, or it can be done by the installation disc. I would give Ubuntu more than 10GB (though that is sufficient to install it), 20GB or more would certainly be better, but that depends on the free space you have available. 

The guide discusses setting your BIOS so that your CD drive boots first, if yours already does then skip that part.

No, installing Ubuntu will not cause hard drive failure, you should be good to go.

Edit: Please read this, also, before you start: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by Mark Phelps on 2009-08-06
ZaM0:

You've done the right thing by shrinking Vista using the Disk Management tool.

How much space you want for Ubuntu depends on whether or not you want to share data files with Vista.  If you want all files in Ubuntu to be private, I would allocate more than 10GB.  If you want files shared, you should be able to get by with less than 10GB -- but then, you'd have to create a shared NTFS partition to hold the shared files -- and that will take some space.

---

### Post by mikechant on 2009-08-07
> You can shrink the D:\ partion from within Windows if you choose to, or it can be done by the installation disc.

> You've done the right thing by shrinking Vista using the Disk Management tool.

Just in case anyone reading this thread wonders why you should use Vista's own tool to shrink its partition/s, when I first installed Ubuntu I used gparted to shrink the Windows partition. When I rebooted into windows, it appeared to stall on startup, but actually windows was busy 'rebuilding' the file system and finally booted sucessfully about 4 hours later. I'm glad I was patient! Other people have reported Vista not booting at all and having to do some sort of manual repair to fix it.

---

