---
title: "Resizing partions on dual boot system"
date: 2010-07-09
forum: New to Ubuntu
---

### Post by Sikas on 2010-07-09
Ive recently made my windows 7 system dual boot with Ubuntu, at the moment i have 4 partitions, my Windows 7 partition, Ubuntu partition, Ubuntu swap partition and an NTFS 'Storage' partition to share files/folders between Windows 7 and Ubuntu. 
  Now since the implementing the dual boot structure ive moved all my music/movies from my Windows 7 partition to my 'Storage' partition thus creating and excess of available space on Windows 7 partition and a shortage on my 'Storage' partition, now i want to resize my windows 7 partition and allocate that space to my 'Storage' partition but cant seem to do it.

this is what my Disk looks like in Gparted  
[IMG]http://img717.imageshack.us/img717/5052/79400336.jpg[/IMG]

---

### Post by Paqman on 2010-07-09
You can't modify any partitions while they're in use, so you'll need to boot up into your LiveCD and run Gparted from there. Right-click on the swap partition and "swapoff" to unlock that.

You should have no problem shrinking your Win7 NTFS partition. Then you'll need to shift your Ubuntu partitions to the left, which can be quite slow. That'll free up room to expand your storage partition.

---

### Post by ajgreeny on 2010-07-09
**NO, NO, NO!**

**Do not use gparted to shrink your windows 7** partition or you may find that it will not boot again.

Gparted was OK with winXP, but has been flaky with vista and win7, to say the least, so it is **_very_** important to use windows own disk management system to shrink that win7 partition.

Defrag your win7 partition at least a couple of times and you may manage to shrink the windows partition from its present size.  You will then need to move the ubuntu partitions sda2 and sda3 backwards on the disk in order to put all the ntfs storage area together as one, which will be a long job, as moving partitions always is.

If you have not done much with your ubuntu yet, the easiest and quickest way to do all this my simply be to reinstall ubuntu from scratch by:-
1.  Shrink win7 with its own disk management system.
2.  Use gparted on the live CD to delete the two ubuntu partitions.
3.  Use gparted to enlarge the ntfs partition into the free space.
4.  Reinstall ubuntu into three logical partitions in the new extended partition at the end of the drive with about 10GB for root, 10GB for /home and the same 4GB swap size you had before.  Ubuntu will run fine from logical partitions, and 10GB for home should be plenty if you are using a separate shared storage partition for all your data files.

Come back again if you need more help with some of my suggestions.

---

### Post by audiomick on 2010-07-09
+1 ajgreeny. Once again excellent advice from that man! :)

---

### Post by Paqman on 2010-07-09
> **ajgreeny said:**
> 
Gparted was OK with winXP, but has been flaky with vista and win7, to say the least, so it is **_very_** important to use windows own disk management system to shrink that win7 partition.


How well documented is this? I've had no problem shrinking NTFS partitions created by Vista.

---

### Post by john newbuntu on 2010-07-09
If you can backup your storage and ubuntu data to an external drive (say using clonezilla from liveCD etc), then after shrinking sda1 as ajgreeny suggested, you could just delete sda2,3,4 and create an extended partition(I'm guessing you may get about 100GB) and your new logical partitions in it.  You could then copy the data back. I recommend Clonezilla because it automatically updates your fstab and grub entries.

Even if you do not have an external disk, you could backup ubuntu to sda1 and then delete sda2 and sda3.  Then shrink sda1 from win and create a new extended partition (you should get over 60GB) Then create a logical NTFS storage partition on it and copy from sda4.  Then drop sda4 and extend the logical to the right, which is less time consuming and safer.  You could then create ubuntu logicals at the end and re-image that from clonezilla.  I am guessing that your ubuntu image would be less than 1.5 GB.

EDIT: paqman, so have I but I have done it only twice.  I remember reading about a few troubles faced by users in this forum.  I am not sure if it was an older version of either parted or ntfs-3g

---

### Post by audiomick on 2010-07-09
> **Paqman said:**
> How well documented is this? I've had no problem shrinking NTFS partitions created by Vista.

Hallo.
I used the win7 tool after reading this:
[https://help.ubuntu.com/community/HowtoResizeWindowsPartitions](https://help.ubuntu.com/community/HowtoResizeWindowsPartitions)

In a nutshell: gparted should work, but the windows tool is there and easy to use, so why not use it?

edit: I might add that I "instinctively" trust gparted a lot more than anything microsoft makes, but given the insular attitude of microsoft, I can see the sense in using their tool to alter their system.

---

### Post by Paqman on 2010-07-09
> **audiomick said:**
> Hallo.
I used the win7 tool after reading this:
[https://help.ubuntu.com/community/HowtoResizeWindowsPartitions](https://help.ubuntu.com/community/HowtoResizeWindowsPartitions)

In a nutshell: gparted should work, but the windows tool is there and easy to use, so why not use it?

Indeed. I began to see (and make) the recommendation to use the native Windows resize tools after Vista came out, when it was an unknown how well Gparted would handle NTFS partitions created by Vista. I think we've got enough experience now to state that it's not really an issue.

---

### Post by maskiepop on 2010-07-09
Guys,

May I join this discusion? 

I am having a fair bit of problems with my dual boot Ubuntu and Win XP. I set up this dual boot way way back. It was then Ubuntu 8.04 and WinXP Home. It took me quite a bit of work then, and no small amount of help from this forum and from others as well, but I did manage to get that done. In my setup, the Ubuntu 8.04 is on an external HD; the WinXP on the internal HD.

This time I am in trouble again. I was trying to upgrade Ubuntu 8.04 to 10.04. The upgrade failed; it left the UBUNTU 8.04 in an unstable state. I cannot get it to boot anymore. WinXP is still ok. 

I now simply want to install the Ubuntu Lynx, but somehow most of the tools I am using seem to hung halfway through the job.

For instance, I set up Unetbootin and the UBUNTU Lynx iso in WinXP as a "frugal install". It boots, but the process hungs at install time of the Ubuntu Lynx in its own partition. In particular, during the resizing of the partition of the second hard drive for Ubuntu Lynx.

My latest attempt is to use Gparted Live Cd to partition the ext HD. That hangs as well. Does any one have any idea why I am having this much trouble partitioning the ext HD so that I can install Ubuntu?

Any thing else that I should look at and try?

TIA

---

### Post by ajgreeny on 2010-07-09
> **Paqman said:**
> How well documented is this? I've had no problem shrinking NTFS partitions created by Vista.
I think perhaps you are right about a simple action like a straightforward shrink of a vista partition from the right hand end backwards, and certainly XP is OK, but I know in the past people who have tried to carry out more complicated partition activities, like moving the start of a vista partition either to the left or right have caused huge problems that meant it was not possible to boot to windows at all without a lot of work repairing the boot management of windows.  If you use the windows own boot management system there is practically no risk of problems, other than those always associated with partition changes of any kind.

It is for that reason that I would stand by my recommendation to make any changes to windows OS partitions of either vista or 7, with its own system utility.  I am only talking of the main OS partition, not any other ntfs partitions used for data.  I don't think there is any problem using gparted for those

---

