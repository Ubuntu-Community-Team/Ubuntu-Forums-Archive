---
title: "Error: no such partition ....... grub rescue&gt;  ???????"
date: 2010-05-19
forum: New to Ubuntu
---

### Post by tahitiwibble on 2010-05-19
The eternal newbie here again guys .......... so sorry to have to ask again for urgent help but ......

I have a newly acquired laptop with a nice dual boot system (W7 and 10.04) and it was all working fine 'til I got curious and wanted to see what the recovery partition looked like so when I got to the boot possibilities screen I chose something like "Vista loader", a few seconds later there was a window appearing with "ERROR" written in huge characters. So I rebooted the computer and got the message in the thread title.

I haven't got a clue what happened or how to fix it! Please can someone help me out?

Big thanks in advance.

---

### Post by Mustard on 2010-05-19
At first glance it seems you have overwritten the Grub bootloader installed by Ubuntu.  This is a pretty common issue for people new to Linux in general.  If you were to search the forum for a HOW TO thread on 'restoring grub' or 'restoring grub with a live CD'.  I'm certain you will find the latest step by step guide on how to restore your Grub bootloader.

To help you wade through the mass of threads on this subject here is a **current** version, so you don't end up looking at earlier ways of doing it.

[https://help.ubuntu.com/community/Grub2#Reinstalling GRUB 2](https://help.ubuntu.com/community/Grub2#Reinstalling GRUB 2) from LiveCD

You will note that there are a lot of lessons and instructions available at the above link.  I would bookmark it, as its a great resource.

---

### Post by tahitiwibble on 2010-05-19
Thanks a million Mustard. :) I'll plod throught the page you pointed me to and mark the thread "solved" when I've got it. Bookmarked immediately :)

---

### Post by srs5694 on 2010-05-19
To me the error sounds more like partition table troubles. After all, it says "no such partition" and the prompt is a GRUB prompt.

I recommend you boot using an Ubuntu live CD or a rescue CD such as [PartedMagic](http://partedmagic.com/) or [System Rescue CD](http://www.sysresccd.org/) and use a command prompt window to type "sudo fdisk -lu" (the "sudo" part may be omitted on some systems) and post the results here. Please post them between "[noparse]```
[/noparse]" and "[noparse]
```[/noparse]" strings to improve legibility. This output will show us what your partition table looks like.

---

### Post by tahitiwibble on 2010-05-19
Good morning srs5694


```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x76692ca8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    30716279    15357116   1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *    30716280   118331255    43807488    7  HPFS/NTFS
/dev/sda3       118334790   625137344   253401277+   f  W95 Ext'd (LBA)
/dev/sda5       159396930   625137344   232870207+   7  HPFS/NTFS
ubuntu@ubuntu:~$
```

---

### Post by srs5694 on 2010-05-19
There's no trace of a Linux partition on your system. This means that one of two things is likely:


[list]
[*]One of your partitions (probably /dev/sda5) is marked incorrectly and should actually be a Linux partition (type 0x82, rather than the type 0x07 it is now). I doubt if this would produce the error you report, but I could be mistaken about that. If so, the fix is relatively easy: You can launch fdisk (minus the "-lu" option) and use its 't' option to change the type code of the /dev/sda5 partition, then use 'w' to save the changes.
[*]Your Linux partition has been deleted from the partition table, and possibly replaced by something else. On the hopeful side, I notice a gap at the start of your extended partition: The space between sectors 118334790 and 159396930 is unoccupied. It could be your Linux partition(s) belong there.
[/list]


Chances are the second hypothesis is correct. Unfortunately, I can't promise you'll be able to recover your partition(s). You should first assess each option for yourself. Do you have a separate Windows data partition? If so, it's unlikely that /dev/sda5 is a mislabeled Linux partition. Do you know where your Linux partition(s) were in relation to your Windows partitions? If so, and if they were at the start of the extended partition and prior to a Windows partition, chances are they've been deleted and nothing else was changed. If you think this makes sense, try running the testdisk program. It's designed to detect and restore partitions that have been mistakenly deleted. It might do the job, but I can make no promises. It might work quickly or it might take several hours to work.

Before you do anything else, though, I recommend you back up your current partition table. Check the "Final Conversion Thoughts" section of [this Web page](http://www.rodsbooks.com/gdisk/mbr2gpt.html) for instructions. If you attempt repairs and make matters worse, at least having a backup may help you get back to the current state.

---

### Post by tahitiwibble on 2010-05-19
[IMG]http://i221.photobucket.com/albums/dd79/wibble_01/Screenshot--dev-sda-GParted.png?t=1274306313[/IMG]

srs5694,

Thanks for being there. I was copying the above photo while you were writing your answer.

Working from the top line in the shot above; the first unallocated partition was always there and I have no idea why, the second line is the W7 recovery partition into which I tried to boot when the stuff hit the fan, third line is the W7 OS partition, fourth line is a second strange small space, sixth line is where the 10.04 OS is and the bottom line is my "data" partition which I was sharing between the 2 os's.

All I did was to try to boot into the recovery partition so I hope that everything is still in place.

---

### Post by tahitiwibble on 2010-05-19
In the hope that it will help someone to get me up and running, the whole story is this;

I have only had the laptop for 2 days, it came with W7 Pro already installed.
I was curious about W7, wanted to try it out and made it shrink it's own partition to about 40 gigs and then installed 10.04 on it's own 18 or so gig OS partition with /home pointing to the rest of the computer's 320 gig HD. There was a "recovery" partition of about 15 gigs which was called "Vista loader" in the grub menu, also a couple of other  strange and very small partitions.

I have been able to boot to 10.04 and W7 perfectly since setting up the  recovery partition.

(in the background, a small voice, as if it was about to sink into quicksand, can be heard shouting "Heeeelp")

---

### Post by tahitiwibble on 2010-05-19
If I just reinstall 10.04 onto it's partition, will this solve the grub boot options/screen problem?

Edit* Just reinstalled 10.04 and bingo! Thanks to all for their help and support.

---

