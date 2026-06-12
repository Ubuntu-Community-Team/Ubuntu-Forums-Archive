---
title: "Unable to grow Win7 partition"
date: 2011-06-27
forum: New to Ubuntu
---

### Post by Jetro on 2011-06-27
Hi there!

I want to "grow" my Windows 7 partition. I do this from my Live USB with Ubuntu 10.04 on it, using GParted.
But every time, even though I quit Windows nice and quietly, it gets a warning flag in GParted, and gives me some sort of error. It always seemed to work with XP, where I did exactly the same.

This warning flag on the Windows partition tells me it's impossible to do anything with that partition without getting some sort of error. I've tried two times now.

I could shrink and move the Ubuntu partition, but not grow Windows 7. Does anyone know how I can grow it without getting error messages?

Thanks.

---

### Post by vkbidve on 2011-06-27
Very clear from the error log! Your NTFS partition has some error in it. Fix it first as said in the error message. Then only gparted (or any other partition manager) will be able to resize it.

---

### Post by Gone fishing on 2011-06-27
Doesn't Windows 7 have its own partition tools? I understand shrinking a partition with Gparted can course problems with 7, I guess it would be the same the other way.

[http://www.sevenforums.com/tutorials/2670-partition-volume-extend.html](http://www.sevenforums.com/tutorials/2670-partition-volume-extend.html)

---

### Post by candtalan on 2011-06-27
I have seen this type of problem when the hard drive has failed areas. Be prepared for hard drive fail, just in case.

The Ubuntu live CD had a disc utility, can read SMART (hard drive) data. Worth looking art carefully asap to check.
good luck

---

### Post by Mark Phelps on 2011-06-27
Messing around with using Linux filesystem utilities to modify Win7 partitions is asking for trouble!

You should do the following:
1) Boot into Win7
2) Open up Computer, select the Win7 OS "drive" go into tools and use the option to check for errors.  It will ask if you want do to this on restart.  Tell it yes.
3) Reboot into Win7 -- should then run CHKDSK to fix the filesystem problems
4) May have to reboot into Win7 again.
5) Use Win7 Disk Management utility (NOT GParted) to shrink the Win7 OS partition.
6) Reboot into Win7 after partition shrinkage to allow it to do any needed filesystem adjustments.

---

### Post by Jetro on 2011-06-27
Hey, thank you all for your replies.

Apparently I can't read. I did as it said, ran "chkdsk /f" and rebooted twice. I also followed your steps, Mark Phelps, and I can't believe how easy and fast that was. I had no idea I actually could manage the partitions, especially the Windows partition, from within Windows itself. Again, thanks. :)

---

