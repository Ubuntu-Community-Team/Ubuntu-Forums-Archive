---
title: "Can I Force Ubuntu to a specific Partiton?"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by ZekeMenuar on 2009-01-09
That somes it up.

I have a 120gb HD with Vista on it and two partitions.  

About 11gb is in it's own partition.

During the Ubuntu installation it tries to install in the large partition.  I want it in the small, 11gb partition.

How can I do this?

Thanks

ZM

---

### Post by Messyhair42 on 2009-01-09
have you tried installing? one of the steps in the install in partitioning your HD, if you have multiple partitions and want to dual boot with vista choose manual partitioning durring the partitioning step and use the 11GB partition with a / mount point, you should make a swap partition too. for 11GB you should format it as ext3

---

### Post by computermacgyver on 2009-01-09
If the 11GB partition is empty, I would just delete with gparted, the Windows Disk Utility (Start->Accessories->Administrative Tools, I think), or another partition editor. Then Ubuntu will install into the "free space" on the disk.

There maybe a better way to just select the 11GB partition, but I am not sure right now. You can always select "Manual Partitioning" in the setup and configure everything yourself--I imagine, however, that this would be nice to avoid.

---

### Post by cjv8888 on 2009-01-09
Installing by manual selection is really very easy and preferable.
First of all delete the 11 Gb partition.
Then select to install manually into the 11 Gb free space.
The sizes are of your choosing, but I install about 5 Gb as /
5 Gb as /home and 1 Gb as swap, picking the beginning of the partition each time.

---

### Post by ZekeMenuar on 2009-01-09
I figured it out.  Sort of.

The chain of events went something like this:

Mistakenly uninstalled GRUB, causing both XP and Vista to fail to load.  Much profanity ensued.

Cussed loudly at GRUB
 
Reinstalled Vista
 
Found a free third party partition management program called EASEUS

Merged two partitions 

Installed Ubuntu 

Forgot my login and password

Swore loudly at Ubuntu

Googled and searched for three hours for a hack

Took a break. 

Got a Rockstar

Fixed my Wife's VCR.  Yes we still have VCR's.  Three to be exact.

Booted into Vista 

Used aforementioned free third party software to delete Ubuntu

Recreated and formatted the empty partition

Reinstalled Ubuntu

It's been a real fun morning

Now Ubuntu is in it's own 11gb partition.  Vista is in it's own 99gr partition

Things are where they are supposed to be.  Everything works.

I'm tired

ZM

---

### Post by Amranu on 2009-01-09
That could've all been avoided by just reinstalling grub from a live cd

---

### Post by ugm6hr on 2009-01-09
> **Amranu said:**
> That could've all been avoided by just reinstalling grub from a live cd

Indeed. That journey was unnecessarily convoluted.

Could have saved a fair amount of swearing, searching and money on a Rockstar!

But, I suppose it's the journey not the destination that matters!

Welcome to Ubuntu.

---

### Post by ZekeMenuar on 2009-01-09
> **ugm6hr said:**
> Indeed. That journey was unnecessarily convoluted.

Could have saved a fair amount of swearing, searching and money on a Rockstar!

But, I suppose it's the journey not the destination that matters!

Welcome to Ubuntu.

I sometimes take the scenic route. :lolflag:

---

### Post by linfidel on 2009-01-09
Why would you curse GRUB when it did what you told it to do?  :)

If you knew how easy it is to install GRUB, you would be cursing at yourself for taking the hard way.  You can always boot a live CD if you don't have a grub disk or floppy.  You should know which partition contains the /boot/grub directory - usually the same one as Ubuntu.  
Then, from a terminal prompt, run grub;  if the /boot partition is the 2nd primary partition, these two line will reinstall GRUB:
root (hd0,1)
setup (hd0)
If the /boot directory is in an extended partition, it would be something like hd0,5, or higher.

From the same live CD, you can run gparted and merge, create, delete, format partitions.

I'm pretty sure you can also change passwords for an existing Ubuntu; the login name you can get just by looking at the /home directory.

All those hours wasted reinstalling stuff could have been spent learning something new and useful.  Hopefully, you learned something out of this, if only not to mess around with things you don't understand.  Well, maybe you have a future in VCR repair.  :D

---

### Post by anewguy on 2009-01-09
> **ZekeMenuar said:**
> I sometimes take the scenic route. :lolflag:

Me too!  And I love the Bill the Cat avatar - AAAACCKK PHHHFT! - been a long time since I've seen him!

Dave :)

---

