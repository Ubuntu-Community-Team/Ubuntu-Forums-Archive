---
title: "accidentally deleted /root /boot /dev and the lots"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by z7510000 on 2009-04-28
Hi all,
I accidentally delete the "disk" (a partition where my ubuntu is installed). Most folders were deleted including grub loader stuffs thus i can't boot into anything ubuntu or windows. 

ubuntu liveCD doesn't allow me to install foremost as admin.

I managed to install a new ubuntu on another partition on the same disk. I'm trying to undelete files from the original partition which has all my settings, appls and files... but I can't access the original partition or it's trash. 

I'm quite new to linux. Please help me. Many thanks.

Andy

---

### Post by unutbu on 2009-04-28
How was the partition deleted? The method of deletion affects how or if the partition can be recovered.

Also, in the body of your post, you said a partition was deleted. But in your title it looks like directories within the filesystem were deleted. Clarification would help us. Which one is it?

---

### Post by z7510000 on 2009-04-28
hi unutbu,
sorry for confusion. i was in the system, click into the partition (where ubuntu installed, it's a EXT3) then ctrl-A to select all, then press delete button. it started deleting and after a while I saw it deleting 3GB instead of 2GB capacity memory card, and only then I cancelled the deletion but the system started to look broken where desktop icons were missing, the trash icon disappeared, etc.

I now managed to install Foremost (running on LiveCD USB), but dunno how to undelete files in that partition (/dev/sda6).

Thanks.

---

### Post by b@sh_n3rd on 2009-04-28
The way I understand it, you've mounted separate partitions for /root /boot and /dev is it? And are those the only partions you've deleted? Meaning, you've got others, part of your installation which didn't get deleted? If, when installing, you selected "default" in the partitioner, you would end up with /boot /root and /swap. Unless you are mistaking the names of the folder /dev to be a partition?...this is confusing...:)

**EDIT:** Umm...that explains something...

---

### Post by Hospadar on 2009-04-28
First off, how did you delete this stuff?

If you used "rm" you're basically hosed, it is hypothetically possible to recover files deleted this way, but unless you immediately shut off the computer and made an image of the disk, had a lot of time and knowledge about computer forensics, you're hosed (and you might be anyways even if you had those things).

When you delete stuff in a graphical environment, it generally just gets moved to a folder (which is usually ~/.local/share/Trash
So if you just selected it and clicked delete, or dragged it to the trash, it should be there, but otherwise, a re-install is probably your best bet.

---

### Post by z7510000 on 2009-04-28
> **b@sh_n3rd said:**
> The way I understand it, you've mounted separate partitions for /root /boot and /dev is it? And are those the only partions you've deleted? Meaning, you've got others, part of your installation which didn't get deleted? If, when installing, you selected "default" in the partitioner, you would end up with /boot /root and /swap. Unless you are mistaking the names of the folder /dev to be a partition?...this is confusing...:)

**EDIT:** Umm...that explains something...
sorry for the confusion... i'm new to linux. I only have one partition for that ubuntu, not swap. One partition with everything in there, root /dev /boot /dev etc.

i was using the system as usual after plugging in a USB memory drive, then I mistaken the system partition as the USB drive. I clicked into the system partition  (/dev/sda6, where ubuntu installed, it's a EXT3) then ctrl-A to select all, then press delete button. it started deleting and after a while I saw it deleting 3GB instead of 2GB --- capacity of the USB memory card, and only then I cancelled the deletion but the system started to look broken where desktop icons were missing, the trash icon disappeared, etc.

I now managed to install Foremost (running on LiveCD USB), but dunno how to undelete files in that partition (/dev/sda6).

Many thanks.


BTW, I just tried running Foremost but experienced error:


ubuntu@ubuntu:~$ sudo foremost -w -i /dev/sda6 -o /recovery/foremost
Processing: /dev/sda6
|*******************WMV err num_header_objs=-1073683314 headerSize=1283430543591726241
*WMV err num_header_objs=-1073683314 headerSize=1283430543591726241
***************************Segmentation fault (core dumped)

any idea? thanks.

---

### Post by b@sh_n3rd on 2009-04-28
ahuh. I get it...sorry for not being able to understand :D. I'm not sure of auto recovery though. I made a similar mistake when trying to dual boot with XP. Instead of re-partitioning an HDD i intended for ubuntu, i accidentally formatted my XP partition. Spitty. But your case is strange as well as different. I'd have re-installed even though i'd have been really aggravated with the whole incident. Maybe someone else has a better tip.

---

### Post by z7510000 on 2009-04-28
From LiveCD session, I can see the problem partition (/dev/sda6). It has the following folders:
root, proc, sys, dev, lost+found
however, they are all pretty much empty folders. I can't read the lost+found folder.
Using PartitionEditor, I can see that the partition still has lots of used space, hoping that means files are still there, but simply moved to somewhere (maybe lost+found folder). 

I've installed MagicRescue and Recover, but don't know how to use them.

Please help... do you know how can I access or undelete files from LiveCD session?

Thanks.

---

### Post by z7510000 on 2009-04-28
Thanks anyway. 
Btw, I thought linux is safer and at least won't allow me to accidentally delete the "system"... how stupid of me!

---

### Post by unutbu on 2009-04-28
z7510000, if you used Nautilus to delete files, I think the files end up in ~/.Trash or ~/.local/share/Trash.

Since you must have been running Nautilus as root, the "deleted" files might be in /root/.Trash or /root/.local/share/Trash or /.local/share/.Trash-0.

Here is a way to find all the Trash directories on the system:

Boot from the LiveCD
Open a terminal.
Type
```

sudo mount /dev/sda6 /mnt
sudo find /mnt -type d -name *Trash* 
```

Are you trying to find/recover your personal files (stuff in your home account) or are you simply trying to restore your system?

If you only wish to restore your system, a clean reinstall would be easier.

---

### Post by wizard10000 on 2009-04-28
> **z7510000 said:**
> Hi all,
I accidentally delete the "disk" (a partition where my ubuntu is installed). Most folders were deleted including grub loader stuffs thus i can't boot into anything ubuntu or windows. 

ubuntu liveCD doesn't allow me to install foremost as admin.

I managed to install a new ubuntu on another partition on the same disk. I'm trying to undelete files from the original partition which has all my settings, appls and files... but I can't access the original partition or it's trash. 

I'm quite new to linux. Please help me. Many thanks.

Andy

Oops.

It probably would have been possible to recover the data before you overwrote it - but I've had good luck recovering deleted partitions by just running fdisk and recreating a partition with exactly the same geometry as the deleted one.

Did the partition you installed to overwrite the old partitions or are they still pretty much unmolested?

---

