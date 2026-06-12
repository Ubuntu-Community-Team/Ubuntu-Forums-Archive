---
title: "Resizing extended partition with Gparted?"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by hobo14 on 2009-05-13
I have my laptop running Ubuntu only, and loving it, but need to dual boot xp to be able to run PPStream.

So I started installing windows a little while ago, until it reminded me that it needs a primary partition to be installed on, and I forgot to make one when I partitioned the disk.

[IMG]http://img228.imageshack.us/img228/2311/screenshotdevsdagpartedr.png[/IMG]

I want to put a primary partition and xp where the unallocated space is, so I tried to resize(shrink) sda2, but I can't.  
Gparted just won't let me, the resize command isn't available!

Is there some way around this?  Or some other tool I can use?

---

### Post by drs305 on 2009-05-13
You probably still have the swap file mounted or are trying this from within ubuntu. Use the LiveCD so none of the partitions is mounted. Right click the swap partition to select swapoff and make sure none of the other logical partitions in the extended partition are mounted when you perform this operation.

---

### Post by randyklein99 on 2009-05-13
Just a guess, but it won't let you touch a partition you are actively using.  So I would boot up a Live CD and see if you can do it that way.  Of course, back up all important data first, just in case.

---

### Post by hobo14 on 2009-05-13
Ok, thanks guys, will try the livecd.

---

### Post by hobo14 on 2009-05-13
Live Cd worked great, cheers.

Now I hope I can ask a windowish flavoured question...

[IMG]http://img139.imageshack.us/img139/1365/screenshotdevsdagpartedt.png[/IMG]

Windows won't install to the primary partition sda3 on the right hand end of the disk.  When the XP install gets to the part where it needs to boot from the hard drive before copying more files from CD I just get "Disk Error".

I then fixed GRUB to boot Jaunty on hd0 or XP on hd2, Jaunty boots fine (using it now) but still get "Disk Error" for XP.

Is there some truth to "You can't install windows beyond the first 8(?) GB of the disk"?  Or is it some other problem?

Note: don't let my mounting of sda7 as /windows throw you, that was just for convenience during Ubuntu's install.  That partition isn't related to my troubles with windows.

---

### Post by hexanol on 2009-05-14
Hum, that's weird. I really doubt that Windows XP can't be installed beyond the first 8 GB of a disk (but I do have heard that some old DOS system have this problem).

What's the output of "sudo fdisk -lu /dev/sda" ? Also, try installing Windows XP inside an NTFS partition (well, in a partition holding a NTFS file-system).

---

### Post by hobo14 on 2009-05-15
Hey cheers for the reply hexanol, but I was right, the computer didn't like booting an OS beyond 8 GB.  I shrunk the first partition to 7 GB, moved the other partitions to the the right hand end, and put a new FAT32 partition starting at 7 GB for windows, and it worked fine.
I don't think it's windows, I think it's the computer.

---

### Post by hexanol on 2009-05-15
Glad you resolved your problem.

But next time, you really should use an NTFS file-system for holding Windows, there's only a few good points in FAT32. [And note that you can access (read and write) NTFS file-system from Linux without problem with ntfs-3g.] ;)

---

### Post by hobo14 on 2009-05-16
> **hexanol said:**
> Glad you resolved your problem.

But next time, you really should use an NTFS file-system for holding Windows, there's only a few good points in FAT32. [And note that you can access (read and write) NTFS file-system from Linux without problem with ntfs-3g.] ;)

Maybe only a few reasons but one is a big one for me: no ADS in FAT!  I never use NTFS if I can possibly help it.

---

