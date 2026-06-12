---
title: "Creating extra partition for Ubuntu without formatting drives?"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by wallis2812 on 2009-01-23
Hi

I have installed Windows XP and Ubuntu on my computer. Initially I partitioned my harddrive with a partition each for: Windows, Ubuntu, Linux boot and Linux swap (4 total).

All my documents have been on the NTFS Windows partition and accessed there from Linux. However, this has been causing some problems and I would like to create a separate common partition, probably NTFS for my documents, which both Ubuntu and Windows can access. However, I do not have a spare partition space to create this partition, since 4 have already been used up.

Is it possible to format either the boot partition or the swap partition (am thinking this would be the better one) and then turn it into an extended partition, where the original partition can be recreated along with the new partition. I can resize my Windows partition using GParted to create extra space. However, I have just been worried that when I format the swap partition and then recreate it in an extended partition it might cause problems.

I am trying to avoid reinstalling Ubuntu so want to know if this is possible.

Thanks very much for your help.
From someone who comes from the land where Ubuntu originates.

---

### Post by mjheagle8 on 2009-01-23
if you are creating a new partition or are repartitioning, you have to reformat at least part of the drive. you cannot write in an unformatted partition.

---

### Post by dnRoyston on 2009-01-23
Also, since you are running Windows XP, you can also install Ubuntu as a normal program, simply insert the CD when XP is running, and follow the commands to install it to your drive. No formatting or Partitioning is needed, and you won't even get your hands dirty.

---

### Post by -kg- on 2009-01-23
What you will need to do is boot to the Ubuntu Live CD and use GPartEd from there.

You will need to delete your swap partition (the 4th Primary partition), shrink one or more of your remaining Primary partitions to create the room, then create an Extended partition encompassing the remaining space.

Once you have done this, you can re-create your swap partition inside your Extended partition (be sure to mark the swap mount point), then create your required partition(s) inside the Extended partition.

For further information on partitioning operations, refer to:

[https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition")

---

### Post by dnRoyston on 2009-01-23
Ooh, I just read the rest of your post, and now I understand your problem.


It depends on how much free space you have on each of the partitions. You're going to have to resize one down a bit smaller to give the others room to resize to your liking. So as long as not all your drives are at 99%, you should be fine with GPartEd

---

### Post by wallis2812 on 2009-01-23
Thanks very much for the help. 
I shrunk my windows partition, deleted the linux swap partition and then created a new partition with a shared NTFS partition and a linux swap partition in. It seems to have worked well using GParted. This problem seems fixed.
Thanks again.

---

### Post by mjheagle8 on 2009-01-23
no problem, glad we could help you!

---

