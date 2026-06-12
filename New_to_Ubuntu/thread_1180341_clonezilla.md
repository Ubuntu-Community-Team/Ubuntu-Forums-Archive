---
title: "clonezilla"
date: 2009-06-06
forum: New to Ubuntu
---

### Post by tanha on 2009-06-06
hello,

i've playing aroung with clonezilla. i clone my root partition and everything goes fine. then i try to restore it to another computer, but it fails everytime; it keeps telling me that the image may be corrupt. 

any ideas?

---

### Post by LewRockwell on 2009-06-06
what tells you that it might be corrupt?

---

### Post by tanha on 2009-06-06
> **LewRockwell said:**
> what tells you that it might be corrupt?

clonezilla does. and then it aborts (gives me an option to shutdown,restart,start again, etc...)

---

### Post by pedja_portugalac on 2009-06-12
I have no idea why it is happened to you but I have no problems using clonezilla 1.2.2-14 to make an image of the full hard drive including MBR. Did you create the /home/image??????? directory on your external HD or you have followed clonezilla suggestions? May be you can restore only to computers with exactly same hardware? When I install fresh Ubuntu I always make one backup image as it is for the "in case". You never know but this way you have your fresh install back again in just 3 to 5 minutes. All partitions, user account, everything like in Acronis but much better and faster. After that I make weekly incremental backups and all of this is made for the same computer, my lap-top. I never tried to restore my backup images to different computer. It should be your inattention while choosing and cloning.

---

### Post by tanha on 2009-06-13
Well, I did try to restore the cloned partition to a different hardware configuration/machine; could that be why the image is seen as corrupt ?

---

### Post by pedja_portugalac on 2009-06-13
> **tanha said:**
> Well, I did try to restore the cloned partition to a different hardware configuration/machine; could that be why the image is seen as corrupt ?
Maybe.

Check this page anyway

[http://www.howtoforge.com/back-up-restore-hard-drives-and-partitions-with-clonezilla-live](http://www.howtoforge.com/back-up-restore-hard-drives-and-partitions-with-clonezilla-live)

---

