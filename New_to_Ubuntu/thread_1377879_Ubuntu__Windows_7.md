---
title: "Ubuntu / Windows 7"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by mlthmp on 2010-01-10
Hey everyone! Has been awhile since I've been around these parts. I have a new PC and have a couple of questions for everyone.

I am considering putting Ubuntu on this system, and was wondering if Win 7 and Linux would play well together. I've heard horror stories of people trying to dual boot Ubuntu / Vista, and was wondering if Win 7/Ubuntu would be as bad?

Or, would it be better to say install VirtualBox, and run Linux within Windows..

Which would be my best bet for using both systems? Dual Boot (if possible) or running it within Windows via VB, etc.

---

### Post by running_rabbit07 on 2010-01-10
I am dual booting Ubuntu Karmic and Windows 7 on 2 systems and they are playing nicely at sharing the HDD and boot record. You will want to use Windows to shrink your NTFS partition to make room for Ubuntu. Or if you want to use Ubuntu's partitioner to make the adjustments, you will want to have a repair disk handy, which is easily made by going to control panel, then to the back-up applet and clicking to make a repair disk, which if you don't have one already, it is a god thing to have.

---

### Post by sandyd on 2010-01-10
Alright. 
The first thing is DO NOT DO NOT DO NOT. shrink the partitions using gparted or any of the partitoners on the ubuntu cd. You will require the windows repair disk if you use the ubuntu partitioners.

So...
Boot up windows.
Go into the control panel
Administrative Tools -> Computer Management (or something like this) -> Disk management.

Shrink the drives and leave it as free space.
And remember the "right hand rule" (theirs actually one for physics too, but w/e). A partition can only be shrunk to the left, meaning that if you shrink a partition, the free space will all be on the right hand side of the partition.

Then pop the ubuntu cd in and restart. Start the installation.
When you get to the partitioning stage, choose "use largest block of free space"

done.
have fun with ubuntu!

---

### Post by running_rabbit07 on 2010-01-10
> **carlee said:**
> Alright. 
The first thing is DO NOT DO NOT DO NOT. shrink the partitions using gparted or any of the partitoners on the ubuntu cd. You will require the windows repair disk if you use the ubuntu partitioners.

That is why I explained how to make the repair disk. I have tried downsizing with the Windows technique and been stuck with it offering less than 8 gigs, which isn't enough for a happy install.

---

### Post by talsemgeest on 2010-01-10
> **mlthmp said:**
> Hey everyone! Has been awhile since I've been around these parts. I have a new PC and have a couple of questions for everyone.

I am considering putting Ubuntu on this system, and was wondering if Win 7 and Linux would play well together. I've heard horror stories of people trying to dual boot Ubuntu / Vista, and was wondering if Win 7/Ubuntu would be as bad?

Or, would it be better to say install VirtualBox, and run Linux within Windows..

Which would be my best bet for using both systems? Dual Boot (if possible) or running it within Windows via VB, etc.
They should play very nicely together. Simply install windows first, then run the ubuntu installer, choosing the amount of hard drive space you want for each OS. If you already have ubuntu installed, you can still install windows, but you will need to restore the grub as per this post: [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by Ozitraveller on 2010-01-10
I'm dual booting Windows 7 64 and Ubuntu 9.10 64, and I used gparted to shrink the partitions. Windows knew something had changed the next time I booted, but it went through it's normal disc check and then started the desktop, all ok! And it hasn't complained since then.

---

### Post by sliketymo on 2010-01-10
> **running_rabbit07 said:**
> That is why I explained how to make the repair disk. I have tried downsizing with the Windows technique and been stuck with it offering less than 8 gigs, which isn't enough for a happy install.

Try this the next time:Disable the page file,and superfetch.Restart.Defrag a couple of times.You should be able to squeeze a little more space out of it.

---

### Post by running_rabbit07 on 2010-01-10
> **sliketymo said:**
> Try this the next time:Disable the page file,and superfetch.Restart.Defrag a couple of times.You should be able to squeeze a little more space out of it.

Hopefully, I'll never have do adjust the partitions again.

---

