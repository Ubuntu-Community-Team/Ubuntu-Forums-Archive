---
title: "Partitioning concerns"
date: 2009-05-31
forum: New to Ubuntu
---

### Post by C. M .Hughes on 2009-05-31
Hi all,
I have dual booted by 160GB hard drive with Ubuntu and Vista. I would like to make a partition that will contain files that I can access from both OS. 

From the reading I have done, I understand the following to be true (please correct me if I am wrong, or if there is a better way):

1. I can not do this from inside my Ubuntu installation (as the partitions need to be unmounted), but should do it either using a GParted live CD, or use my Ubuntu live CD.
2. The new partition should be formatted as Fat32 so that it can be read by both Ubuntu and Vista.
3. The new partition would be mounted by all users in Vista. 
4. I could change which users can mount it in Ubuntu.

I plan to create the partition at the end of the Vista partition. My main question is this: will this new partition change the numbering of the current partitions, and therefore will I have to change the /boot/grub/menu.lst file? If so, do I do this from the live CD? If it all goes wrong, will I be able to fix any of it by booting from the 'recovery mode'.

Many thanks, and I hope that this thread hasn't already been addressed somewhere else.

---

### Post by lindsay7 on 2009-05-31
If you shrink the windows partition and add a new one, make sure that you defrag the windows partition first. You will add a partition so you may or may not change the numbering of the existing partition. I guess it depends on how it is set up now. You would just need to edit the grub menu with the new partition numbers if it is a problem.

---

### Post by candtalan on 2009-05-31
Be aware that if partitioning goes wrong it can go wrong in a particularly disasterous way. You will loose everything on the drive! So be careful to have good backups first. If push comes to shove you may need to reinstall everything. I am not saying this is likely but it is easily possible, partition tables are critical things.

FWIW I usually use parted magic live CD.

Existing partition numbering usually does not change, for example if you delete a partition, the others usually retain their numbers. You will need to check this yourself to be sure though?

Be aware that ubuntu may be installed in logical partitions in an extended partion area probably at the end of the drive. The vista partition and any maintenance partition are probably primary partition type, and the extended partition will make a third 'primary' I think.

You are allowed a maximum of four primary partitions only, so if my guesses are correct, then by resizing the vista you could make one new primary partition for fat32.

Alternatively, resize the ubuntu and make another logical partition in the extended area.

hth

---

### Post by -kg- on 2009-05-31
candtalan is substantially correct.

One thing that I can add is that you can resize your Windows (Primary) partition and, if Ubuntu is contained in a Logical partition (i.e., a formatted partition within an Extended partition) you can expand the Extended partition into the space freed then create the second partition within the Extended partition free space as a Logical partition.

You can find out more details on partitioning operations by clicking on the link in my signature block.

Oh, and the partition does not necessarily have to be FAT32...Linux handles ntfs just fine.  I would create the ntfs partition with GPartEd rather than Vista's partition manager, though.

---

### Post by C. M .Hughes on 2009-05-31
Thanks to everyone for the information. For anyone interested I have attached a screenshot of my current partition table. Dell put the sda1, sda2, and sda5 on there as default.

From what you're saying, it seems like it might be good to resize the Windows partition (sda3), extend the Ubuntu partition (sda4), and then create a new logical partition within that. My only question is, will Windows be able to read it?

---

### Post by -kg- on 2009-05-31
Yes, and yes.

Of course, sda4 isn't your Ubuntu partition.  That would be sda7 (with sda6 as your Ubuntu swap partition), which are logical partitions.  What you would be doing is extending your Extended partition and creating another logical partition in the unallocated space within it.

You are forced to do this because of the "4 Primary Partition" limit.  You may only have 4 Primary partitions on a physical hard drive.  Dell had already included 3 (Dell Utils, Recovery, and the OS partitions) and the Extended partition makes the 4th.  If you tried to shrink the OS partition and create one without extending the Extended partition, you would be unable to.  (Go ahead and experiment with it...it won't hurt anything because you won't be able to do it.  See the Wiki page in my signature block)

An Extended partition is a special type of Primary partition in which you can create a great many extra partitions, called Logical partitions.  If my memory serves me, Linux can handle up to 63 Logical partitions on a drive.  As long as you expand your Extended partition and create your new partition within it, you'll be good to go.

And yes, Windows will work with a Logical partition.  I did that for quite a few years before I got into Linux, from Win98 on through the various distros.

---

### Post by C. M .Hughes on 2009-06-01
Many thanks for your response -kg-, I think I now have a better understanding of how I am going to achieve this file share partition. I'll repost after I've completed it.

---

### Post by White Rasta on 2009-06-01
> **C. M .Hughes said:**
> Hi all,
I have dual booted by 160GB hard drive with Ubuntu and Vista. I would like to make a partition that will contain files that I can access from both OS.

This could be easily accomplished via usb hbd formatted to fat32 without upsetting your system and risking data loss

---

### Post by C. M .Hughes on 2009-06-18
Success! For anyone interested, here are the steps I did:

1. Defragged the Windows partition (using defraggler)
2. Booted using Ubuntu Live CD so that no partitions were mounted
3. Reduced Windows partition by 20GB which gave 20GB of free space in my extended partition.
4. Formatted unallocated space to FAT 32
5. sudo gedit /etc/fstab and added the following line to the end so that the partition mounts at boot:

/dev/sda8       /media/disk vfat user,rw,auto,umask=0000,uid=1000,gid=1000,iocharset=utf8	0       0

Attached is a picture of my new partition set up. Thanks for all of your help everyone, I'm excited about having this file share.

---

### Post by sbalaji.vkb on 2009-06-20
Guys, I'm trying to install UBUNTU 9.04 as fresh install. I have 4GB of unallocated space which I wanted to use in addition to existing partitions and could not access it with any of the available disk utilities for windows (I tried EASEUS home edition 4.0, BootIT, Active@killdisk etc). Only Active @ killdisk displays this partition as unallocated, but could not do anything with it like formatting, merging etc. Anyhelp is appreciated.

[IMG]file:///C:/Documents%20and%20Settings/Balaji/Desktop/screenshot.JPG[/IMG]P.S. I could not attach the screenshot of the active killdisk here. Any permissions for newbie?

---

### Post by Moop on 2009-06-20
The Ubuntu live cd has a partition editor on it. You could boot from the live cd and use that. You could also make a gparted bootable  cd that works well for partition editing. [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

I'm not sure about windows but with Ubuntu you are limited to 4 primary partitions on a hard drive and won't be able to create a new partition if you already have the max amount.

---

### Post by C. M .Hughes on 2009-06-20
Why not boot from the Ubuntu Live CD? Once you have, you will have the option to install- you'll need to choose custom install to tell it which partition you want it to use.

EDIT:
My apologies for not reading Moop's response first

---

### Post by LewRockwell on 2009-06-20
this one is a charmer: [http://partedmagic.com/](http://partedmagic.com/)

---

