---
title: "Ubuntu on USB stick with low memory"
date: 2011-05-09
forum: New to Ubuntu
---

### Post by mlm198 on 2011-05-09
Hi,
 
I am new to Ubuntu and have installed it on a 16Gb USB drive. It was working fine but now it says it is low on memory despite the fact there is 12Gb left. Is this because the Ubuntu on a USB stick runs in RAM so is limited to how much RAM there is?
 
Thanks in Advance for any help.
 
Matthew

---

### Post by mikewhatever on 2011-05-09
Don't think Ubuntu from USB can utilize as much space as 12GB. How do you know that it really has access to that space? Can you show some evidence? Can you post the output of df -h.

---

### Post by bodhi.zazen on 2011-05-09
> **mlm198 said:**
> Hi,
 
I am new to Ubuntu and have installed it on a 16Gb USB drive. It was working fine but now it says it is low on memory despite the fact there is 12Gb left. Is this because the Ubuntu on a USB stick runs in RAM so is limited to how much RAM there is?
 
Thanks in Advance for any help.
 
Matthew

How did you install it exactly ?

---

### Post by mlm198 on 2011-05-10
Hi,
 
Thanks for the replys. I installed it on a blank USB stick which I formated before hand. It seems to show the space when I click on the explorer (probably not the correct linix word). 
 
I made in windows using the instructions on the Ubuntu website i.e. use the universal USB installer (I also used persistance ??). 
 
I don't mind installing it again as I had only just started playing with it I just want to check that there is no intrinsic reason it should not use all the space. Is there?
 
Matthew

---

### Post by oldfred on 2011-05-10
the USB installs are for installing Ubuntu. I think there is a limit on how large the persisent file can be.

Pros & cons of persistent install over direct install to flashdrives 
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

You can do a full install, just like an install to a sdb drive. I have it in a 8GB partition with some of room and then a 8GB data partition. Some of the same rules as an SSD apply but it will of course be slow bothdue to USB port and flash speeds. Minimizing writes helps a lot.

It does not have to be encrypted:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)

Use ext2 or ext4 without journal:
tune2fs -O ^has_journal /dev/sda1
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

You want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.
SSD’s, Journaling, and noatime/relatime 
[http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/](http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

---

### Post by bennachie on 2011-05-10
With the present setup, as far as I can determine, the liveCD image and the persistence file together are, in practice, limited to 4GB. That is really quite adequate if all you are doing is preserving some settings across multiple hard disk installations.

If you actually want a portable operating system, and don't plan to carry out further hard disk installations, you would be better off installing Ubuntu properly to the stick. 16GB is about the minimum realistic size for this kind of thing, and its probably a good idea to install without a swap partition.

---

### Post by C.S.Cameron on 2011-05-11
If you like the Live system but need more than 4GB persistence, delete the casper-rw file and make an ext2, (or 3 or 4), partition and name it casper-rw.
(if you want a separate home folder also make another partition and name it home-rw.

Don't use all of your extra space for persistence if you want to be able to save data to the drive from a Windows computer as Windows can only see the first partition on a flash drive.

---

### Post by mlm198 on 2011-05-14
I will try doing a full install to my USB as suggested.

Thanks for your help

Matthew

---

