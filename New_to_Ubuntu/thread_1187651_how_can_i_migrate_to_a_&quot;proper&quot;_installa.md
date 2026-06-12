---
title: "how can i migrate to a &quot;proper&quot; installation?"
date: 2009-06-14
forum: New to Ubuntu
---

### Post by pous on 2009-06-14
i'm really new here, been using linux for under a week... downloaded jaunty(9.04) did the wubi installation and loved it, my question is:
-is there a way for me to do either a proper partition or full installation out of my existing wubi virtual partition **without** losing the configuration and changes i've done?

---

### Post by nandemonai on 2009-06-14
> **pous said:**
> i'm really new here, been using linux for under a week... downloaded jaunty(9.04) did the wubi installation and loved it, my question is:
-is there a way for me to do either a proper partition or full installation out of my existing wubi virtual partition **without** losing the configuration and changes i've done?

One way would be to use [remastersys]("http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html").

Honestly though, if you haven't done much customization then a backup of /home and a proper reinstall would likely be easier.

I've not attempted this myself as I steer clear of wubi but in theory it can be done.

---

### Post by H2SO_four on 2009-06-14
I would backup /home and do a full install from the live CD.

---

### Post by freeman2000 on 2009-06-14
Would you like to save time and problems down the road?  As has been stated, back up /home and do a fresh install.  Wubi is an emulator running in the Windows environment - most likely NTFS partition.  In Ubuntu you will be creating a different environment for it's partition - either the ext3 or ext4 file system.  Since you are doing a clean install, I would recommend going with the ext4 file system, as it is the future of Linux. 

I would also recommend preparing your hard drive.  Before installing Ubuntu, wipe all unnecessary/unwanted/unneeded files from the Windows (NTFS) partition.  Run your antivirus program and some spyware programs to make sure the hard drive is clean.  Then run check disk to resolve any disk problems.  Finally, run a defragmenter program.  Now you're ready for the clean install.  This will help you down the road.  

Finally do the fresh install from the Live CD.  Take your time and follow the instructions closely, especially for partitioning.  Good luck.

---

### Post by H2SO_four on 2009-06-14
if you are concerned about "cleaning" the drive before you install something else, I would recommend using DBAN.  Its a disk wiping program.  Then use Ubuntu LiveCD.

---

### Post by pous on 2009-06-14
wiping the drive that is not much of a concern for me unless its actually needed...
about the customization i have changed the themes from pretty much everything except cursors and icons, installed a bunch of fonts, 2 or 3 apps, and most importantly was having a lot of trouble with online multimedia and finally got it solved... and if possible i'd rather just "move" everything than do it all again.. 
freeman2000 i didnt understand the part of the file system...
 
i stumbled upon [this]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?") i'll check it out later... i'm not really in a hurry to do the partition and all, but rather now than later that i may have more files and stuff...

---

