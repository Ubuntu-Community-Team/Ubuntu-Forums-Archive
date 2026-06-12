---
title: "I tried to uninstall, now all messed up."
date: 2009-01-04
forum: New to Ubuntu
---

### Post by weetoots on 2009-01-04
I have Ubuntu on a separate drive, Windows on another.

I tried to uninstall 8.10, info found here said use live CD and delete partion. Ok, did that, now GRUB won't let me get to Windows.
GRUB error message: GRUB Loading stage 1.5
GRUB loading, please wait.....
error 17. 
Ok, I understand this GrUB is looking for the partitions I deleted.

How can I get rid of this GRUB message?
Should I just re-install Windows and this grub will be deleted?
I have no access to my burner, so I can't make a Super GrUB tool.

Gees,what a mess.

Where can I find the proper way to uninstall Ubuntu 8.10
properly? 

Thanks

---

### Post by sledge73 on 2009-01-04
reinstall windows & partition the disk the way you want it set up. windows likes to be on it's own partition!! make sure you leave room for ubuntu!!!!!! then install ubuntu!! do not shrink the windows partition unless your using vista!! xp wont let you shrink it without errors!!! let me know how this comes out!!!

---

### Post by wmoore on 2009-01-04
What are you trying to achieve? Were you uninstalling Ubuntu in order to just go back to Windows? Or were you planning on re-installing some other distro?

---

### Post by Michael.Godawski on 2009-01-04
sledge73 you don't have to use the exclamation mark that often. :D

weetoots you can try the super grub disk and select "fix windows boot"

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by gandaran on 2009-01-04
you can reinstall windows, but you don't have to, just fix the grub, use the windows disk, boot the disk find the prompt option and type **fixmbr** or use super grub disk recovery [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by weetoots on 2009-01-04
What am I trying to achive?
1. Remove Ubuntu from the wifes computer and remove the GRUB dual boot.
2. Change from 8.10 to 8.04.1 on my computer.

I want to access Windows because Linux (Ubuntu) does not have a driver for my Logitech 9000 Pro web cam. I use Skype. 

I have the Super GRUB disk, so I will try that.


I have Windows on 1 HD, with 3 partitions and Ubuntu on a different HD.

Thanks for the replies.

---

### Post by wmoore on 2009-01-04
> **weetoots said:**
> 
1. Remove Ubuntu from the wifes computer and remove the GRUB dual boot.
Well either the supergrub disk or booting from a Windows CD and choosing recovery, then running 'fixmbr' should sort you out here.

---

### Post by kansasnoob on 2009-01-04
> **gandaran said:**
> you can reinstall windows, but you don't have to, just fix the grub, use the windows disk, boot the disk find the prompt option and type **fixmbr** or use super grub disk recovery [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

+1!

I don't think the OP mentioned whether this was XP or Vista and the procedures differ slightly, but for sure *a reinstall is not necessary!*

[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

[http://www.winvistatips.com/fix-mbr-a116.php](http://www.winvistatips.com/fix-mbr-a116.php)

That's just for a start!

---

### Post by weetoots on 2009-01-04
Thanks,
It is Win XP, don like Vista. I will try now.
TNX

---

