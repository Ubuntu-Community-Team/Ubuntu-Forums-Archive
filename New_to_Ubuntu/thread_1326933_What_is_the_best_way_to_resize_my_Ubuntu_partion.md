---
title: "What is the best way to resize my Ubuntu partion ?"
date: 2009-11-14
forum: New to Ubuntu
---

### Post by Ubu2010 on 2009-11-14
I have Ubuntu 9.10 installed with 177GB on a 640GB dedicated to it. I want to steal some room from Windows and give it to Ubuntu. How would I go about that ? Thanks :)

---

### Post by drs305 on 2009-11-14
I wrote this guide for a slightly different situation but it still explains how to take space from Windows (or another partition) and give it to Ubuntu. You can skip the first two or three sections, which explain how a new install may have ended up too small to work.

[Expanding an Ubuntu System Partition]("http://ubuntuforums.org/showthread.php?t=1219270")

---

### Post by pastalavista on 2009-11-14
The best way I've found to resize partitions is with the Ubuntu live CD. Boot it up to the desktop (Try without changes) and open System-> Administration-> Gparted. Make sure none of the HD partitions are mounted (right-click "unmount drive") And then use the resize option to shrink the Windows drive and expand the Ubuntu drive.

---

### Post by Ubu2010 on 2009-11-14
Thanks for the replies ! :D

---

### Post by anewguy on 2009-11-14
As, I hope, a carry-on to this, what if you want to do the opposite - you want to shrink the Ubuntu partitions?  I made my root and home a LOT bigger (well, in my terms - I don't have the huge drive that some have) than I really needed to, and I'd like to have a side-by-side install of another distribution as well.

How would I shrink my current partitions, and will grub somehow be updated (this new grub where the menu.lst doesn't exist anymore) so that I can also select to boot the other distribution?

Thanks in advance!
Dave :)

---

### Post by chriscross93 on 2009-11-14
> **pastalavista said:**
> The best way I've found to resize partitions is with the Ubuntu live CD. Boot it up to the desktop (Try without changes) and open System-> Administration-> Gparted. Make sure none of the HD partitions are mounted (right-click "unmount drive") And then use the resize option to shrink the Windows drive and expand the Ubuntu drive.

+1. GParted on a live cd always workd easily and quickly for me.

---

### Post by drs305 on 2009-11-15
> **anewguy said:**
> As, I hope, a carry-on to this, what if you want to do the opposite - you want to shrink the Ubuntu partitions?  I made my root and home a LOT bigger (well, in my terms - I don't have the huge drive that some have) than I really needed to, and I'd like to have a side-by-side install of another distribution as well.

How would I shrink my current partitions, and will grub somehow be updated (this new grub where the menu.lst doesn't exist anymore) so that I can also select to boot the other distribution?

Thanks in advance!
Dave :)

The process would be the same. The link I provided uses the LiveCD method. If you are going to *shrink* the partitions and not delete them, you shouldn't have too much trouble, especially if you are using UUIDs in /etc/fstab and that is what is listed in /boot/grub/grub.cfg. 

If you have the choice, make the new partitions at the end of the device so your original ones don't change designations (sda1, sda5, etc). If everything is designated by UUIDs, it really shouldn't matter, which is one of the reasons UUIDs were introduced.

After you have created the new partitions *but before you reboot*, run the following commands and make sure the UUIDs or device designations are still correct:
```

sudo blkid -c /dev/null  

```
Compare them with those in /etc/fstab. In /etc/default/grub, check and make sure this line includes the # symbol:
> 
**#**GRUB_DISABLE_LINUX_UUID=true



After you have rebooted, GRUB 2 should find new OS's by using "sudo update-grub". If you have any problems and it doesn't, start a thread of your own and we can help you find any new installs.

---

### Post by Zoot7 on 2009-11-15
For resizing partitions I rather the gparted liveCD.
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by Puzzled Guy on 2009-11-15
use gparted from the live cd and if you shrink any partitions, don't shrink it past that yellowish section of the rectangle representing the partition because that yellow part is you DATA!

---

