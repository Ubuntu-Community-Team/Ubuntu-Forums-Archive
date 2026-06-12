---
title: "Does Samba have a practical limit on file size's it can cp??"
date: 2007-08-16
forum: Networking &amp; Wireless
---

### Post by kevdog on 2007-08-16
Trying to copy large files > 1.4 Mb (if that is large) using samba from linux to windows box -- using cp command.  Directory on windows box is mounted on linux box.  Im finding that about every other attempt fails with INPUT/OUTPUT error.  Ive googled around and found people having similar errors, however with much larger file sizes (ie .iso files).  Nothing is showing up in dmesg suggesting a network error.  

Do I need to resort to scp instead of samba to copy these files?  It rather annoying to say the least.

---

### Post by ihristov on 2007-08-17
1.4 MB is nothing. I have copied files > 1 GB
There is a limit < 2 GB on certain setups that use file systems which can't handle files > 2 GB

Not sure why you are having these issues.

scp or pscp from the Putty package will do the trick. You can use key authentication if this is a scheduled task.

---

### Post by MetalMusicAddict on 2007-08-17
I've copied DVD-9 (8.5GB) images across my network. Linux->Linux and Windows->Linux. No problems in 2 years. Drives are NTFS and EXT3.

---

### Post by kevdog on 2007-08-17
I know I not copying big files -- its from a wireless laptop to a wired computer.  I get a bunch of Input/Output Errors also -- maybe thats the cause of the problem.  Its weird however if I try again the file will copy without a problem.  I noticed that I also get a burst of activity - where a whole bunch of data will be transferred, then nothing for 30-45 seconds, then more.  Im not sure what else I can do other than use a different method, however I thought a mounted samba directory would be the most direct, so there is no overhead wasted with encryption.

Any thoughts how I can debug this problem.  (I tried unison/rsync with same results).

---

### Post by ihristov on 2007-08-19
> **kevdog said:**
> I know I not copying big files -- its from a wireless laptop to a wired computer.  I get a bunch of Input/Output Errors also -- maybe thats the cause of the problem.

Input/Output errors might indicate a problem with your hard disk. Examine these more closely and try to fix these first.

Another issue might be the wireless. Try using wired connection to isolate the issue.

---

### Post by kevdog on 2007-08-20
Ive tried copying directly from the flash drive (plugged into USB port) ----> wireless connection >> LAN client, and through copying the flash drives contents to the wireless computer hard drive ---> Wireless connection ---> Wired computer.

Im not saying its definitive buts its probably not the hard drive.

Could be the wireless connection, however ssh (scp) seems to work without incident.

Based on this, it seems Im left to conclude its a Samba problem

---

