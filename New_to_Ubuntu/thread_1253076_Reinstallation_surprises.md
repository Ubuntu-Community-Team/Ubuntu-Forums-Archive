---
title: "Reinstallation surprises"
date: 2009-08-29
forum: New to Ubuntu
---

### Post by stratprof on 2009-08-29
Acer Aspire One (hard disk)
Netbook Remix (Jaunty), fully updated; Windows XP dual boot

My initial Ubuntu was small as I anticipated only using Linux to access e-mail while at my university. I fell in love with Ubuntu, started adding goodies and suspect that my last additions pushed things a bit too far. I was faced with a system that had neither upper nor lower panels. I found forum instructions on recovering the panels but error messages pointed to problems beyond my newbie capacities.

I decided to simply reinstall UNR, this time with a larger space allocation.

All went well; I'm updated and functioning perfectly.

This was, however, my first Linux reinstallation. I thought everything would be overwritten. It apparently did not happen this way.

 My new GRUB startup screen has changed. The current/latest kernel (what I call "15") plus the original kernel ("11") are my first options. My XP setup is below these. These are all as they should be but...

I have, however, a startup menu that shows the history of my original setup history (i.e., the original kernel, the update to "13", "14" and "15".)

I investigated using gparted. My new setup is on sda7 (swap on sda8). The originals were on sda5 (swap on sda6).

I used gparted to allocate SDA5, 6, 7, and 8 to sda3. Other than the sda6 swap, all are locked when I view them with gparted.

Bottom line: I suspect my original, corrupted installation is still sitting on sda5. I suspect this is why I'm seeing the extraneous information at startup.

I can't get to sda5 to clear out the directory. 

Is my diagnosis right regarding the source of the GRUB directory quirks? Any ideas how I might clear out sda5 and simply reallocate the space to sda3?

OR .. should I simply leave well enough alone? The housekeeping issue doesn't seem to affect the performance of the reinstalled system (beyond simply eating a bit of hard disk space).

Many thanks in advance for any guidance.

---

### Post by SunnyRabbiera on 2009-08-29
Usually if you see extra entries in Grub such as Kernel A, Kernel B and Kernel C its nothing to worry about.
Usually these extras kernel entries are created by kernel updates, but there is always another entry listed as a "just in case" because sometimes new kernels dont pick up the hardware you have and other issues.
These extra entries usually have no effect on space though.

---

### Post by drs305 on 2009-08-29
> **stratprof said:**
> 
I used gparted to allocate SDA5, 6, 7, and 8 to sda3. Other than the sda6 swap, all are locked when I view them with gparted.

Bottom line: I suspect my original, corrupted installation is still sitting on sda5. I suspect this is why I'm seeing the extraneous information at startup.

I can't get to sda5 to clear out the directory. 

Is my diagnosis right regarding the source of the GRUB directory quirks? Any ideas how I might clear out sda5 and simply reallocate the space to sda3?

It looks like your original partitions were retained during the reinstall. Grub found your original installation and now reports those as additional boot options.

In gparted, you can't do anything on a mounted partition. Mounted partitions have a "Keys" icon to the left, showing they are mounted. You must umount them before you can delete/move/resize them. To do this, highlight the partition, then select Partition, Unmount.

If there is nothing on the old partitions you want to keep, you can delete them. Before you can combine 5 (a logical partition) with any primary partition, you must delete it, then shrink the extended partition to get the unallocated space outside the extended partition.

I wrote a guide on expanding /. The situation is different but the principles on how to move things around are the same. It is linked as "Expand /" in my signature line.

If you still have questions, post a gparted screenshot and tell us what you would like to do.

---

### Post by stratprof on 2009-08-29
Thank you very much for responding.

Your information, and the accompanying article, were very informative.

I unfortunately had problems implementing your advice.

I was able to unmount sda5 and unswap sda6. I could delete neither, however. I received an error message indicating a need to first delete lower-numbered partitions.

I next booted from a USB disk and tried to delete the partitions. (There is data, by the way, in sda5.) i received the same error message.

Your clear advice in the article inspired me, however, to at least try resizing the partitions I seem unable to delete. All looked excellent: reduce the old swap (sda6) to a minimal size, reduce sda5 in a similar manner, expand the new swap (sda8) and the new "main" partition (sda7) to take over the now free space ... 

I clicked apply, crossed fingers, and the process stopped immediately. I saved the information explaining the process failure but, as a true newbie, I've absolutely no idea where it's now located. (Sorry.)

Any follow up advice would be much appreciated.

A first place this newbie wonders about: is it possible to manually renumber the partitions?

Once again, thank you.

---

### Post by stratprof on 2009-08-29
My apologies for not including the screenshot you mentioned in your reply. I've attached it to this note.

I'd like to remove sda5 and sda6, then allocate the free space to sda7 and sda8.

My previous note detailed the problems I've experienced doing so.

At the risk of sounding like the proverbial broken record ... thank you.

---

### Post by drs305 on 2009-08-29
OK, because of the parition numbering, you must do the partitioning work from the LiveCD or another CD such as the SystemRescue CD (see link below).

The reason is that before you delete a partition, all partitions with a higher number must be unmounted. Since your system partitions are 7 and 8, they must be unmounted before you can delete 5 & 6. You must use the LiveCd or equivalent to allow you to do this.

Edit: Composed before previous post was uploaded.

What type of USB disk were you using? I normally use either the LiveCD or a SystemRescue CD when I do repartitioning work. The SRCD is located here:
[http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page")

I have not seen a message saying lower numbered partitions must be deleted first. There are two messages that are fairly common: a partition must be unmounted before you can do anything with it; all partitions with a *higher* number must be unmounted before a lower number partition can be unmounted.

Can you post a snapshot of the gparted image you are seeing? You can take a snapshot via Applications, Accessories, Take Screenshot.

By the way, welcome to Ubuntu!

---

### Post by stratprof on 2009-08-29
This is quite a welcome, indeed, to Ubuntu. Thank you for your time and help.

I burned a live ISO to the USB. I launched gparted from the live ISO/USB.

I'll first try booting again from the live ISO/USB, this time making doubly sure sure all the relevant pieces are unmounted. If this fails, I'll try the rescue disk.

I'll post my results, whatever the are.

BTW: I'm sincere when I say "thank you for the welcome." It's really nice to have expert guidance in this process.

---

### Post by stratprof on 2009-08-30
A final update. The problem has been resolved and my installation is now as desired.

My system is updated, I've a Linux partition that's large enough to suit my future needs, and Windows (the other resident of my dual boot setup) isn't complaining.

My overview (for the benefit of those who follow)...

Undue caution made me fearful of adjusting things in gparted. I had inadvertently left elements of the extended partition mounted when i tried making changes.

The solution I settled upon, ultimately, was a crude one: I deleted all existing partitions and simply started from scratch. I now have a GRUB startup menu that's as clean as it was when I first stepped into Linux.

In the process, though, I learned some lessons that other newbies might find helpful:

* It seems gparted will not overwrite an existing installation. It will instead put down new swap and data partitions. (If there's a way to force an overwrite, I could not find it in the partition manager's interface controls.)

* gparted doesn't seem to handle multiple instructions. It deleted partitions perfectly. When told to expand AND move a remaining partition, and then do something with the other remaining partition, it's an understatement to say things crashed and burned. 

From my experience: newbies beware. Do one thing at a time when working with gparted. 

[LIST]
[*]Resize a partition as a step; wait till this step is complete before doing anything else.
[*]Then move the new partition as a separate step; wait until it's complete before moving forward.
[*]Then expand the remaining partition as yet another separate step. Again, wait until this is done before manipulating the disk further.
[/LIST]

* finally, a big lesson learned is that the user must explicitly tell gparted how much space to allocate to ensure a partition that's "right." The partition table may be daunting but letting gparted make its own decisions, the path I essentially followed from my first installation through to the end of this journey, can lead to undesired outcomes. Learn to use the partition table. (This comes back to that "fear thing" I mentioned at the start of this note.)

Many, many thanks to the two forum participants, drs305 and SunnyRabbiera, who dove in to guide a struggling newbie.

---

### Post by LewRockwell on 2009-08-30
[http://ubuntuforums.org/showthread.php?t=1222961](http://ubuntuforums.org/showthread.php?t=1222961)

.

---

