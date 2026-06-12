---
title: "Switching from Vista to 9.04, question about data on hard drive."
date: 2009-06-22
forum: New to Ubuntu
---

### Post by anuj016 on 2009-06-22
I've decided that I want to switch from Windows Vista 32-bit to Ubuntu 9.04 on my Lenovo laptop. I already have the CD I ordered from Canonical, and have booted of the CD and played around with Ubuntu enough to make the decision. 

My questions is this: I currently have two NTFS partitions on my hard drive -  C (~29 gigs total, less than 2 gigs free) and D (~105 gigs total, about 17 gigs free). C has Vista on it, which I want to wipe out and replace with Ubuntu, whilst D has all my media files (mostly music). If I install Ubuntu woithout a dual boot (which I don't want because I really want to be rid of Vista) will it wipe out both C and D, or just C? I do have most of my media files on D backed up on my iPod and another desktop, but would rather not have to spend time transferring them back to the laptop if I can install Ubuntu without affecting them.

Any help for a newbie would be appreciated!

---

### Post by billgoldberg on 2009-06-22
> **anuj016 said:**
> I've decided that I want to switch from Windows Vista 32-bit to Ubuntu 9.04 on my Lenovo laptop. I already have the CD I ordered from Canonical, and have booted of the CD and played around with Ubuntu enough to make the decision. 

My questions is this: I currently have two NTFS partitions on my hard drive -  C (~29 gigs total, less than 2 gigs free) and D (~105 gigs total, about 17 gigs free). C has Vista on it, which I want to wipe out and replace with Ubuntu, whilst D has all my media files (mostly music). If I install Ubuntu woithout a dual boot (which I don't want because I really want to be rid of Vista) will it wipe out both C and D, or just C? I do have most of my media files on D backed up on my iPod and another desktop, but would rather not have to spend time transferring them back to the laptop if I can install Ubuntu without affecting them.

Any help for a newbie would be appreciated!

Your C and D drives (in Linux we don't use numbers to indicated the drive) are two different partitions.

When you install Ubuntu, just tell it to use the 29gb partition.

The other partition will not be touched.

*It must be noted that NTFS is well supported in Linux, but it would be better to use etx3. But that would require you to back up the data on your 105gb partition and then put it back afterwards. It might not be worth the trouble. The reason I say this is because EXT3 hardly fragments at all, while NTFS is famous for it fragmentation. *

---

### Post by anystupidname on 2009-06-22
Ubuntu will only affect the C partition unless you specifically TELL it to wipe the second D partition in the install wizard. For your reference, "C" will likely become "/dev/sda1" and "D" will be "/dev/sda2"

---

### Post by anuj016 on 2009-06-22
Thanks for your prompt replies!


> **billgoldberg said:**
> 

*It must be noted that NTFS is well supported in Linux, but it would be better to use etx3. But that would require you to back up the data on your 105gb partition and then put it back afterwards. It might not be worth the trouble. The reason I say this is because EXT3 hardly fragments at all, while NTFS is famous for it fragmentation. *

That's great to know! I will probably be investing in a new external hard drive (my old one crashed after 2 yrs of great service) in the near future to back up all those files, and when I do I will probably switch to ext3.

---

### Post by anuj016 on 2009-06-22
Looks like I still need some help.:(
 I'm at Step 4 of 7 whilst installing Ubuntu 9.04, and the options available are:

- Install Ubuntu/Vista side by side i.e. dual boot (which I do not want)
- Use the entire disk i.e. wipe out everything including the partition with my saved files (which I also don't want)
- Specify partitions manually (so this should be what I choose, right?)

I choose the third option, and am shown three partitions:
- sda1 (~29GB, this has vista on it currently)
- sda5 (~105GB, this has my backup files)
- sda3 (~12GB, I have no idea what this is) 

First I tried to choose linux-swap for sda1 and leave the others untouched but no matter what combination of partitions I choose, I get the following error message: "No root file system is defined. Please choose this from the partitioning menu."

What does this mean? Does it have anything to with the Mount Point option under the Edit Partition menu?

---

### Post by anuj016 on 2009-06-23
<bump>

---

### Post by 0x40 on 2009-06-23
Yes you do want to specify the partitions manually. Based off of your last post it looks to me like you didn't define a root partition. Unlike Windows, Linux needs two partitions to run. Root and a Swap.

So your C drive (Vista to be wiped) you will want to set as a ext3 and mount it as "/". Your swap partition, you will set as "swap" and you want the amount ~double your ram. So if you have 2gigs of ram your swap should be ~4gigs (You can get away with using the same amount of Swap as you have ram. [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq))

I would delete both your C drive and the unknown 12gigs partitions so they combine into one large "free space" partition. Once that happens you can create new partitions and assign the sizes you want for both Root and Swap much more easily.

Before attempting this, you may want to wait for someone else to back me up on this, I just started using Ubuntu today but everything I have just said I did earlier today and it is working flawlessly.

---

### Post by anuj016 on 2009-06-23
Thanks so much! I have it up and running, and love it. I used that whole unused portion for the swap, and the first partition as ext3. Thanks again!

---

### Post by paul_be on 2009-06-23
> **anuj016 said:**
> Thanks so much! I have it up and running, and love it. I used that whole unused portion for the swap, and the first partition as ext3. Thanks again!

Its good to hear that your up and running, if I understood correctly you have a 12GB swap partition???  For future refernce, the rule of thumb is make the swap twice the size of your ram.  I guess more does not necessarily hurt it just may be wasted space.  If you are happy with your install you may not want to mess with things though.  Anyway congrats and have fun!!!

---

### Post by meindian523 on 2009-06-23
And most likely,that 12G partition was your recovery,which is of no use since you didn't want Vista anyway.Please mark the thread as solved.

---

### Post by anystupidname on 2009-06-27
Hehe, as the others have mentioned, a 12GB swap partition is rather ridiculous. This is easily remedied.

-System>Administration>Partition Editor (if that option isn't available, "sudo aptitude install gparted", in a terminal first)
-Then, assuming sda3 and sda5 are adjacent, right click on sda3 and pick "swapoff" and right click on sda5 and unmount.
-Then resize sda3 to something between 1-2GB (depending on RAM) and expand sda5 to take up the newly recuperated free space.
-Then remount both partitions.

If you'd rather increase the size of your Ubuntu partition (sda1), it would be slightly different because it cannot be unmounted. You could use [Unetbootin PartedMagic]("http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=240127")

If you're all set after this, edit the title of your first post and add [Solved] to it.

---

