---
title: "How to reshuffle partitions"
date: 2010-03-05
forum: New to Ubuntu
---

### Post by Nachums on 2010-03-05
The table below shows the partitions on my laptop (running 9.10) after I deleted the XP partition (sda2), formated it and mounted it on /storage.
The PC boots and so far so good. 
I now want to shrink or eliminate sd2 and increase the size of /home (sda7) and / (sda6) but the swap partition is in the way. 
What is the best to reshuffle the partitions so that the swap will be at the end and the whole disk is share by / and /home?

Thanks for a brief explanation or a pointer to a doc or thread.
 
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           4       32098+  de  Dell Utility
/dev/sda2               5        3022    24242085   83  Linux
/dev/sda4            3023        4864    14795865    5  Extended
/dev/sda5            3023        3095      586341   82  Linux swap / Solaris
/dev/sda6            3096        4581    11936263+  83  Linux
/dev/sda7            4582        4864     2273166   83  Linux

---

### Post by -kg- on 2010-03-06
By the description in your post, I will assume that you already have an understanding of fstab and GRUB issues in manipulating partitions on your hard drive, so I'll be more than happy giving you the partition manipulation end of things.  You can find more detailed information on manipulation of partitions at the link in my signature block.

I suggest using either an Ubuntu Live CD or a GPartEd Live CD for these partitioning operations.  I prefer the [GPartEd Live CD.]("http://gparted.sourceforge.net/livecd.php")  Also, I'm sure I don't need to tell you that you should make a backup of everything you don't want to lose, since partitioning operations *can* go wrong!

I see that you have two primary partitions...sda1, which is a Dell Utility partition, and sda2, which is your present /storage partition.  After that, you have sda4, which is an extended partition (again, see the link in my signature block) which contains the rest of the logical partitions, sda5, 6, and 7.  sda 5, which is your swap partition, is the one you want to move to the end of the disk, and you want to shrink/eliminate sda2 and take the rest of the disk for your root and /home.

I personally would take these steps *_one at a time_*, letting each step complete before taking the next one.  While you can program several steps and then apply them, I have had one or two bad experiences with that method and don't really like to do it.

First (needless to say) you want to shrink or delete sda2.  This will give you the room you need to move and expand your other partitions.  Do whichever you decide to do.  If you want to delete the Dell Utility partition, I assume you can do that, too.  This is usually a recovery partition (Windows) that you won't really need (unless you anticipate that you might want to recover Windows.  I don't really know how these "recovery partitions" work, personally).  That will give you even more room on your hard drive.  I'm sure I don't need to tell you that this will also change the partition numbering scheme and will have to be dealt with in fstab and GRUB once you're finished.

Now, the rest of your partitions are logical partitions, contained in an extended partition.  This is perfectly fine, since Linux will boot from and run in a logical partition (contained within an extended partition).  In order to gain the room that you freed up by shrinking/deleting sda1 and or sda2, you will next need to expand sda4 (the extended partition).  You cannot move a logical partition outside of an extended partition; you must increase the extended partition into the space you freed.

Once you have done this, you will want to delete the swap partition.  You cannot move a partition past another partition.  The only way to do this is to delete the partition and recreate it in the order you want it.  Of course, this operation is also going to change your partitioning sequence.  The swap partition contains no information and is safe to delete and recreate.

Then you will need to move your sda6 partition (root or home?) to the beginning of the extended partition.  Once you do this, then move the other partition over just enough so that you have room to recreate your swap partition to your desired size behind it.  Then create your swap partition in that space.

Once you have done all this, you can expand your other partitions into the remaining space as desired.  Note that all these operations will change partition designations and partition IDs rather radically, and as I said above, GRUB and your fstab file will have to be edited.  If you're not sure on this subject, then I'm sure that someone will be along that has more expertise than I in this area.

If it were I that was doing this, I would just back up my critical information, delete partitions, recreate them, and reinstall and re-set up Ubuntu, but that's me.  I store the vast portion of my critical data external not only to my "/" and "/home" partition, but external to the hard drives on my computer, on an external drive.

At any rate, with your partition scheme, that is how you need to proceed if you want to preserve and resize your partitions.  Remember, back up your data; if possible, all your partitions.  And note: several of these operations are going to take a *considerable amount of time!*  Don't freak out and stop the operation part-way through; it will hose *at least* that partition, and possibly the whole drive (which is why I suggest applying *one operation at a time.*).

A plus would be to do this with a UPS; an even *bigger* plus would be to do it with an emergency backup generator.  Once these operations are started, they *_cannot be interrupted._*  If they are, you will minimally hose the partition, and likely the partition table along with it.  It is *_very important_* to back up your critical data; a plus would be to make an image of your partitions with a tool like [Clonezilla]("http://clonezilla.org/") ([Here is an excellent tutorial]("http://www.dedoimedo.com/computers/free_imaging_software.html") on it's use).  Hopefully you have an external hard drive or thumb drive on which to store the image.

Then, in the event of a disaster, you can recreate the partitions in the desired size and position, and reload the images to the partitions.  You can probably do this in the first place and just delete and recreate the partitions in the desired positions, but I'm not sure about this, since I've never done it.

My tutorial in my signature block will give you more detailed information on partitioning operations and what you can expect.

---

### Post by HermanAB on 2010-03-06
Hmm, got to agree with the sentiment of doing a fresh install posted above - that is what I would do too.  

While it is possible to shuffle partitions to some degree, it is almost guaranteed that something will go horribly wrong and then you have to re-install anyway...

---

### Post by Nachums on 2010-03-07
Thanks guys for the replies. 
The enormity of the task scared me a bit so I went back to basics. Since the reason for wanting to expand the partitions was lack of space, I first went ahead with massive cleanup, and freed up enough disk space to remove all immediate pressure.
Still, I took your advice and will likely do a new install when 10.04 is released.

---

