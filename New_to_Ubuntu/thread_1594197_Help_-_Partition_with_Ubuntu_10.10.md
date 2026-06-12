---
title: "Help - Partition with Ubuntu 10.10"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by Perun84 on 2010-10-12
Hello,
I should start out in saying that I have absolutely *no* experience with Linux whatsoever. I only decided to install it last night after Windows 7 Starter on my new laptop got the better of me.
I consulted a few people, and their talk seemed reasonable, but now appears to have been a bit high for me. They told me to mount a partition because I shouldn't lose my Windows 7 (why ever, but I can't argue with computer people). So that is what I am trying to do now. My problem is that all the help available, or at least all that I have found (such as [https://help.ubuntu.com/community/HowtoPartition/ResizingPartition](https://help.ubuntu.com/community/HowtoPartition/ResizingPartition)) appears to be for earlier versions. I downloaded Ubuntu 10.10 32 bit, and this seems to be for an earlier version.

Put simply, I'm stuck with this screen, and I have absolutely *no* idea what do do now:

[IMG]http://i315.photobucket.com/albums/ll464/Perun666/Bildschirmfoto.png[/IMG]

Everything I read there is Greek to me. As you might expect, you will have to talk to me like to a fourth grader. I'm completely helpless.

Thanks in advance!

---

### Post by ft-Orchard on 2010-10-12
What the screen is trying to tell you is the new lay-out for your hard-disk.
The big orange bar is the new Ubuntu installation, and the small blue bar is the current Windows installation. 

I think it looks good, if you want to keep your Windows installation and do as much as possible with Ubuntu (e.g. Office/Mail/Internet etc.). But, if you still want to play games on Windows, I'll suggest making the blue bar somewhat larger.

Know what, just make the blue bar larger.
-- choose /dev/sda2 and click "edit". Now change the value 232582 to 175000, Apply new setting.
-- choose /dev/sda3 and click "edit" Now change the value 17157 to 74739, Apply new setting.

You do not have to change anything else.
The numbers represent disk space. So 232582 is 232 GB of disk space. 
If you applied the settings you wil have a Windows disk of +/- 75 GB. This should be enough to play some new games and have plenty of space left. 

If the blue bar looks larger, you can install Ubuntu. At the start-up of you computer you will now have the choice between Ubuntu and Windows.

---

### Post by lotharmat on 2010-10-12
Ignore this- I'm talking out of my ****!

---

### Post by Perun84 on 2010-10-12
Thanks so far... I changed the values as ft-Orchard suggested. Right now, I want to have Ubuntu and Windows side-by-side.
Now, when I click "Install Now", it tells me that no root file system is defined and that I should correct this from the partitioning menu. Err... how do I do that?

---

### Post by ft-Orchard on 2010-10-12
Choose /dev/sda2 and click "edit" set the mount point to "/" (forward slash). Apply settings.

The / mount point is the root mount point. In Windows terms (if you can even compare it) it's the "C drive". You don't have drive letters in Linux. Just "mount points". For example, you can mount "/home/your_name" (which is your personal directory) to a separate partition. 

Press Install now.

---

### Post by ft-Orchard on 2010-10-12
An ideal situation should be having a boot and swap partition also.
But, deal with that when you are more experienced. If I where you, I should dig up an old computer somewhere and mess around with an Ubuntu install. If you like to go deep, try a Linux Arch installation (they have great guides) [http://wiki.archlinux.org/index.php/Beginners%27_Guide](http://wiki.archlinux.org/index.php/Beginners%27_Guide)

---

### Post by Perun84 on 2010-10-12
Ah, I'm starting to understand. That "mount point" thing was what confused me the most. Now, apparently I first need to define what I want to use this partition as before I can enter the mount point. A mate of mine told me I would need a "swap partition", is that what I want it to be? Or if I want to use it as the partition for the OS itself, what do I need to select?

EDIT: Maybe it helps if I say what options I have: Ext3 and 4 journaling file system, Ext2 file system, ReiserFS journaling file system, btrfs journaling file system, JFS and XFS journaling file system, FAT16 and 32 file system, ntfs and swap area.

---

### Post by ft-Orchard on 2010-10-12
**IMPORTANT.** As I can see now, there is not an Ubuntu partition available. 

+ Change /dev/sda2 to 75000, apply. You now have a Windows partition of 75 GB.
+ Now click "add" and add an "EXT4" partition of 154582 (154 GB). Set mount point to "/".

EXT2 / 3 / 4 are partition types. Just like NTFS of FAT is used by Windows. 
swap is a special partition type. 
So, your root mount point must be "EXT2 / 3 / 4" (if you have the EXT4 available, select it)

If you are not sure about swap, add it, see below.
You can create a swap partition if you want. But practically you only need it when you want to hibernate your computer. If you do not want to hibernate (sleep and power off) you should just install Ubuntu.

A rule for swap partitions can be 1.5 times your memory. So if you have 2GB of memory add a 3GB swap partition, but this can be discussed.

3 GB = 3000 (value)

+ Now click "add" and set the type to "swap" instead of "ext2" and add value of 3000, apply

---

### Post by ft-Orchard on 2010-10-12
You do not need a boot partition, that does already exists (/dev/sda1)

---

### Post by Perun84 on 2010-10-12
Sorry to annoy, but it won't let me click "Add...". The only thing I can do is click "New Partition Table..." when I highlight /dev/sda. Should I do that?

---

### Post by ft-Orchard on 2010-10-12
Could you post a screenshot of the screen that you see if you click "New Partition Table..." ?

---

### Post by Perun84 on 2010-10-12
[IMG]http://i315.photobucket.com/albums/ll464/Perun666/Bildschirmfoto-1.png[/IMG]

---

### Post by arubislander on 2010-10-12
The New Partition Table option will erase your entire disk if you OK it. (Clicking on it will give a warning) I don't think that's what you want.

In fact I don't think you should be in this screen at all for what you want to do...

You should go back a screen and choose the option to install Ubuntu side by side with windows.

---------
Edit: Now I see you already have 4 primary partitions created. That is the maximum. If you need all those partitions you will not be able to install Ubuntu side by side with Windows. If you can do without one of the partitions then delete one and create a logical partition in its place. But you might need to find out first which partition is used for what. Have you backed up your data? And do you have means of restoring that back-up in the event of disaster?

---

### Post by Perun84 on 2010-10-12
Yeah, everything is perfectly backed up, and I also have the recovery disk from the purchase. No problem with taking risks, I would just rather have it work the first time. ;)

---

### Post by ft-Orchard on 2010-10-12
> **arubislander said:**
> The New Partition Table option will erase  your entire disk if you OK it. (Clicking on it will give a warning) I  don't think that's what you want.

In fact I don't think you should be in this screen at all for what you want to do...

You should go back a screen and choose the option to install Ubuntu side by side with windows.



lol. So that option IS available :)

@ Perun84: If you still want to proceed, select the "free space" I guess its beneath /dev/sda2. 
and than click "change" and edit as I suggested.

-- edit: If 4 primary partitions is the max. well... the guide for creating logical ones could be somewhat larger :(

---

### Post by arubislander on 2010-10-12
The free space under /dev/sda2 is identified as unusable, because of the 4 primary partition maximum.

Perun84: Do you know what all those partitions are for? e.i. Do you have 4 drives in Windows 7? What's on each of those drives?

---

### Post by Perun84 on 2010-10-12
OK, things seem to be working now. I'll get back here if there's any further problems, but so far thank you very much for your help and patience. :)

EDIT: I had three partitions in Windows, I think the fourth one was the one I created in the beginning of my Ubuntu installation.

---

### Post by Perun84 on 2010-10-12
As a precaution, I have a feeling that what is described here [http://ubuntuforums.org/showthread.php?t=1593799](http://ubuntuforums.org/showthread.php?t=1593799)
will be happening to me. I'm quite uneasy about the fact that the only answer to the thread mentions partition problems...

EDIT: Yes, that is exactly what happened. Now what?

---

### Post by arubislander on 2010-10-12
I'm downloading the iso to get a better idea of what you're facing...

---

### Post by arubislander on 2010-10-12
I've posted the solution in the other thread, but here it is for archival purposes. The username should be all lowercase letters.

---

### Post by ft-Orchard on 2010-10-12
I'm glad things are working now!

---

### Post by Perun84 on 2010-10-12
Everything is running smoothly now. Thank you very much. :)

---

