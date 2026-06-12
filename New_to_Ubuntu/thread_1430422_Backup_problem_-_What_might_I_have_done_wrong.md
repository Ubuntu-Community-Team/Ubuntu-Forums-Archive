---
title: "Backup problem - What might I have done wrong ?"
date: 2010-03-15
forum: New to Ubuntu
---

### Post by HappyShark on 2010-03-15
Laugh if you must, but seriously, could use some expert advice.

I would like advice on two things.  1) Is the cause of my error obvious - if so, what is it? 2) If I cannot recover the noted files, ... is there an easier way to undelete or recover folders from an ext4 device? 

I need to recover roughly 70 Gb of data from an ext4 device that contains other data, will not dismount, and from a linux based desktop. 


Desktop Host: Ubuntu 9.10 64-bit
8Gb RAM
AMD Phenom x4 CPU

drives:
sda (contains all of Ubuntu desktop except /home) ext4
sdb FAT
sdc (/home) ext4

I've been using the system with the OS for about two weeks.  Over the past few days several programs have updated.  We experienced a power outage on Friday that my WIndows 7 vm was not happy about... Rather than fight with it right now, I opened up a different Windows vm.  Nothing seemed really wrong until yesterday (14-Mar).  Yes, legit up-to-date OS's. 

I had a WinXP32x vm open.  While a search program was running the vm locked up, then the desktop locked up completely.  After a lengthy wait I see that the vm had closed and an error message had appeared.  It said something like the directory was out of space.  I suspect that the directory in question is a temp area for the search and it was maxed out.  I decided not to do that again,... emptied the trash.  ... Time to make a backup even if I didn't have things just right yet.  Installed a backup agent and configured to run later that evening.  

I check the system this morning and there were no messages.  The backup appears to have run, but only for about 5 minutes, and does not contain two of the folders that were configured to backup.  Those two folders are now missing from the directory.  Each of those two folders contained multiple sub-folders, and all-tolled roughly 70Gb of data and media.  Would very much like to recover the folders and everything in them, trash and all. 

From CLI tried to dismount /dev/sdc1- and received a message that the device was busy.   Ran lsof and did not see any files open that were related to a vm or anything at all on the /sdc device.  The backup agent, if it matters, is "simple backup" and it was the first time I had used it.  It was configured to send the backup to the /sdb device.  Some files did backup but the set is useless to me.

Bottom line - two key folders disappeared.  Not sure what I did but need to recover the folders soonest as my vm's and current schoolwork are in the missing folders.  I have a "foremost" query running now - it will likely take all day, dang it.  If not, I can rebuild from a previous backup.  Bigger question now though is learning what I did wrong so that I do not repeat it.  

Thank you.

---

### Post by J V on 2010-03-15
If its not in lost+found, download testdisc and try to recover the data (From what I've heard its very good)

---

