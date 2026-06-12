---
title: "Seperate Partitions"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by acai32 on 2009-01-27
I've been researching the basics to installing linux for the past few days and after deciding on Ubuntu, I have a few questions.

 I've read that it would be wise to install /home on it's own partition. The reason for this would be so that if for some reason I had to reinstall Ubuntu, my files and settings would be safe. 

I read these two guides on dual-booting Linux on a machine with Vista ([http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1)  and  [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)), but neither really addresses how to give the /home its own partition. Perhaps I'm reading really out of date documentation ([http://www.control-escape.com/linux/contents.html](http://www.control-escape.com/linux/contents.html)), but maybe this is no longer required?

  Another question is how do I know how large each partition should be? Assuming the above documentation is not extremely out-of-date, what are some rules of thumb on the size of the root, home and swap partitions?

---

### Post by Boomhauer on 2009-01-27
if you want to make separate /home and / partitions, you will need to make 3 separate partitions from your vista partition.  before you start making partitions, it would be a good idea to defrag  your vista partition a couple of times to get everything condensed down.  once you have done this, you can create the partitions with the ubuntu live cd by booting it to a desktop and then going to system>administration>partition editor.  
as far as partition sizes go, 10 gb should be fine for your root (/) partition
then alocate as much as you want to /home.  this is where the bulk of things are stored in ubuntu so you may want to go big here if you think youll be using it alot.  as far as swap goes, if you plan to hibernate the system youll need to have as much swap as you have ram, so if you had 2gb of ram, make 2 gb of swap.  if no hibernation and you have sufficient ram you could get by with 500mb-1gb.  ive got 2gb of ram and ive never seen swap used more than 100mb.
once you get your partitions lined up and you are ready to install, in step 4 of the install, youll need to select manual partitioning and then double click the listings for each of the partitions you have made and select the mountpoint for them.  you would use / for your root partition, /home for the home partition and for swap, click the dropdown box and select 'use for swap' for a basic setup, you could just format the partitions as ext3.  any more questions be sure and post back.
EDIT:  make sure and back up all of your stuff before you start doing this.  partitioning isnt complicated, but it can be a beast to recover if things dont go as planned!

---

### Post by mikewhatever on 2009-01-27
> **acai32 said:**
> 
I read these two guides on dual-booting Linux on a machine with Vista ([http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1)  and  [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)), but neither really addresses how to give the /home its own partition. Perhaps I'm reading really out of date documentation ([http://www.control-escape.com/linux/contents.html](http://www.control-escape.com/linux/contents.html)), but maybe this is no longer required?

While it's never been required to have a separate home for Ubuntu, some think it more convenient, since, if you have to reinstall, there is no need to format home. Guides usually present the simplest way of partitioning, probably trying not to over complicate. Anyway, you'd have to either go with the manual partitioning option, or create the desired partitions even before the installation with gparted.

 >  Another question is how do I know how large each partition should be? Assuming the above documentation is not extremely out-of-date, what are some rules of thumb on the size of the root, home and swap partitions?

There aren't any rules, the partitions shouldn't be too small, the rest is up to the user. For example, if I had a 120 GB hdd, I'd give 10 - 20 GB to root, about 1 GB to swap and about 40 GB to home. The rest would be a backup/storage partition.

---

### Post by cdtech on 2009-01-27
It's always good practice to have separate partitions for system / user. In a multi user environment, this eliminates the user's ability to create hardlinks. Only symlinks can be created across filesystem boundaries, which point to filenames rather than inodes. Just food for thought.

Hope this helps ya.....

---

### Post by acai32 on 2009-01-27
Thanks for the fast responses. I'm currently backing up my info, if I have any trouble with the install or partitioning, I'll let you know.

---

### Post by poltiser on 2009-01-27
I'm not super expert, but maybe it will help you:
1. hardware - I use 64 bit processor, 1 gig RAM 3 HD (80+160+80), printer, tablet Nisis, webCam;
2. software: WinXP Home SP3; Ubuntu 8.1 AMD64; Acronis Disk Director with OS Selector to manipulate the boot of the system (Grub sometimes goes astray);
3. partitions: HD1-1 ntfs (WinXP) + 3 ext3 (usr, root, var); HD2-2 2 ntfs (windows data files) + 1 ext3 (home)+swap; HD3 ntfs (windows data) + ext3 (temp).

It works for a year with about 15 diferent Linuxes and now for a month with Ubuntu 8.1 (WinXP <-> Ubuntu read & write each other).

The only hardware I did not managed to make useful is scanner HP scanjet 3670...

Good luck.

PS. all operations on partitions are done by Acronis Disk Director, because gparted gives sometimes conflicts in setting of partitions - it saves time.

---

### Post by acai32 on 2009-01-28
So, I created 3 new partitions but it seems like it's taking waaaaaaaay too long. It's been going for almost 4 hours now and it lists an estimate of 8 hours remaining. I gave it 100gb to /home, 10gb to root and 4gb to swap. Is something wrong or does partitioning always take this long?

---

### Post by talsemgeest on 2009-01-28
> **acai32 said:**
> So, I created 3 new partitions but it seems like it's taking waaaaaaaay too long. It's been going for almost 4 hours now and it lists an estimate of 8 hours remaining. I gave it 100gb to /home, 10gb to root and 4gb to swap. Is something wrong or does partitioning always take this long?
Simply creating new partitions should take a minute or two at most. However, if you are resizing a partition as well, and the partition is fragmented, then it can take a while. But even then, it should not take 12 hours, so there might be something wrong. However, whatever you do, DO NOT stop it, or restart until it is done.

---

### Post by acai32 on 2009-01-28
It's a 750gb drive. I defragmented the drive before resizing the partition with vista on it and creating 3 new partitions in gparted. I hit apply and then it started chugging along. It said 3 hrs estimated to finish, but then it reached that goal and listed an 8 hr estimate time, so maybe it's only listing the 8 hour estimate for the one operation it's doing at the moment. 

Either way, it seems like my only option is to wait...right?


edit: I checked the detailed listings and it seems to be performing "copy 1255137281 sectors using a blocksize of 4096" (within the "filesystem move" submenu) extremely slow. In fact right now it is stopped, though it was transferring slowly a while ago.

---

### Post by talsemgeest on 2009-01-28
> **acai32 said:**
> It's a 750gb drive. I defragmented the drive before resizing the partition with vista on it and creating 3 new partitions in gparted. I hit apply and then it started chugging along. It said 3 hrs estimated to finish, but then it reached that goal and listed an 8 hr estimate time, so maybe it's only listing the 8 hour estimate for the one operation it's doing at the moment. 

Either way, it seems like my only option is to wait...right?


edit: I checked the detailed listings and it seems to be performing "copy 1255137281 sectors using a blocksize of 4096" (within the "filesystem move" submenu) extremely slow. In fact right now it is stopped, though it was transferring slowly a while ago.
Ok, well it seems like you did something wrong. It should certainly not be copying anything, let alone taking 12 hours to do it.

---

### Post by acai32 on 2009-01-28
Well, I'll try to run through what I did so I can figure out where exactly I went wrong. I was running Vista Home premium 64-bit and I put in the Ubuntu Live cd and rebooted. From there I opened Gparted and there was one primary partition and about 2mb of unallocated space. So, I resized the primary partition to where I now had 114gb of unallocated space. Then from the free space I created 3 new primary partitions, all in the ext3 file system. One was 100gb in size (/home). One was 10gb in size (root). And one was 4gb in size (swap). The swap file was actually in a file system called "linux-swap" and not in ext3. After I doubled check to make sure everything looked right, I hit apply and it started on its so far 16 hour trip. As of now it's apparently on "Move /dev/sda1 (vista's partition) to the left and shrink it from 598.62gib to 584.63gib" with 3 and a half hours remaining. 

I have absolutely no idea what I did wrong.

---

### Post by philinux on 2009-01-28
Leave it to finish. Resizing it what really takes a looooong time.

---

### Post by talsemgeest on 2009-01-28
> **acai32 said:**
> I have absolutely no idea what I did wrong.
You should have resized vista's partition using vista's partition manager, then simply created the partitions using gparted. It is the resizing that takes up the time.

---

### Post by acai32 on 2009-01-28
Just coming back to note, everything installed perfectly. Just trouble with the video card and wireless, but ill make a sperate thread. Thanks for all your help!!

---

### Post by egalvan on 2009-01-28
> **acai32 said:**
> Just coming back to note, **everything installed perfectly.** Just trouble with the video card and wireless, but ill make a sperate thread. Thanks for all your help!!

Congratulations, and welcome to the club! :)

As for the loooong wait to re-size a large NTFS, yeah, been there, done that.
Re-sizing a large 500gb drive took hours.
Now I just move the data to another drive, delete the original, and re-do... much faster.
Live and learn.

ErmestG

---

### Post by talsemgeest on 2009-01-28
> **acai32 said:**
> Just coming back to note, everything installed perfectly. Just trouble with the video card and wireless, but ill make a sperate thread. Thanks for all your help!!
Glad you got it working! :)

---

