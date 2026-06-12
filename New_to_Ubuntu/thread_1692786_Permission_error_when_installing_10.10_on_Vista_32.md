---
title: "Permission error when installing 10.10 on Vista 32 bit"
date: 2011-02-21
forum: New to Ubuntu
---

### Post by Droid-Xer on 2011-02-21
First post guys. I've been trying to get Ubuntu 10.10 up and running on both a Win7 64 and a Vista 32. I keep getting permission errors after about 2.5 hours of install. Any help would be appreciated. If I'm being an idiot let me know! Here's a pic. Thanks
 
[IMG]http://i1236.photobucket.com/albums/ff448/Droid_Xer/Capture.jpg[/IMG]

---

### Post by Gixxy on 2011-02-21
Burn the ISO, boot from the CD and install it from the CD with a dual boot.
Just make sure when you get to the partitioner that you specify the right amount of space you want each OS to have.

---

### Post by Droid-Xer on 2011-02-22
Ok. So burn the 10.10, then leave disc in, and then reboot?

---

### Post by Mark Phelps on 2011-02-22
If you allow the partitioner to shrink your Vista or Win7 OS partition to make room for Ubuntu, you're asking for trouble!

You first need to boot into a LiveCD, open a terminal, and enter "sudo fdisk -lu" (that's a lowercase L, not a one) -- to see the list of partitions already allocated on your drive.

IF you already have four primary partitions, it's going to be a LOT of work installing Ubuntu to its own partition because you're already at the limit of partitions.

If you don't have four primary partitions, use the Disk Management utility in Win7 to shrink the Win7 or Vista partition to make room for Ubuntu.

---

### Post by Gixxy on 2011-02-23
I think he has multiple machines not one with vista and win 7.

He probably has one partition on each machine. (Or a recovery and primary) With that setup I have never had an issue with the partitioner. 

If in doubt take an image of the drive with Shadow protect, acronis or ghost or similar. (I would suggest an image backup anyway... especially if you are unfamiliar with linux)

Or swap out your production drive for an old laptop drive or a new one for that matter hard disk space is on the cheap right now.

As long as my hard disk has plenty of space I would defrag the windows side and let the partitioner do the work for me.

But to answer your original question... yes. Set your bios to boot to CD first and boot to the CD to install. 

[http://ubuntuforums.org/images/smilies/new_popcornsmiley.gif](http://ubuntuforums.org/images/smilies/new_popcornsmiley.gif)

---

