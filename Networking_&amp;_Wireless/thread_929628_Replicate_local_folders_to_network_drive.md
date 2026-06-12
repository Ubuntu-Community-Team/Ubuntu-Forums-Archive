---
title: "Replicate local folders to network drive"
date: 2008-09-25
forum: Networking &amp; Wireless
---

### Post by neiljohnford on 2008-09-25
I'd like to automatically replicate some folders (e.g. music, photos) on my laptop to a network drive over a wireless network (using either smb or ftp). Basically I'd like to save files locally but have my laptop regularly scan for new files and upload them to the network drive - so that another laptop can access them (and also I've got a backup). I've thought about using backup software but this seems overcomplicated - to access the files from the other computer I'd have to restore them from the backup software. Is there a way to just regularly replicate my folders on the network drive (say at startup) so that they show up in my network shares?

Or is my thinking back to front - is it better to save everything to the network drive and take local backups so that I can still use my files when I'm not on the network?

Any ideas gratefully received!

---

### Post by prshah on 2008-09-25
> **neiljohnford said:**
> I'd like to automatically replicate some folders (e.g. music, photos) on my laptop to a network drive over a wireless network (using either smb or ftp). 


You're looking for rsync; there are too many options so```
man rsync
``` will get you started.

Once you've got the command working as you want it, you can stuff it into a cron job for it to be done automatically.

Post back if you want more details instructions.

---

### Post by eldragon on 2008-09-25
or a simpler multiplatform solution is unison, which comes with a gui too. its in the repos.

can be automated through a cronjob too.

---

### Post by neiljohnford on 2008-10-06
Thanks both for the suggestions. I gave Unison a go first as it looked alot simpler to use. However - I struggled to use it with Samba so had to give up on it in the end. 

In the rsync GUI I can see all of the Samba (or FTP) shares that I have mounted - which makes things easier. I spent a long time trying to work out why successive syncs seemed to be updating the same files - then I realised that my network drive does not support preserving the timestamp of copied files - that and the fact that the clock on the drive was set to the wrong time meant that it was constantly thought that the files on the drive were older than the local files. Now that's sussed it works! All I have to do is fine tune the options and work out how to put it in a cron job and I've got a working sync to my network drive. Thanks again! Neil

---

### Post by adonet on 2011-07-17
> **neiljohnford said:**
> Thanks both for the suggestions. I gave Unison a go first as it looked alot simpler to use. However - I struggled to use it with Samba so had to give up on it in the end. 

In the rsync GUI I can see all of the Samba (or FTP) shares that I have mounted - which makes things easier. I spent a long time trying to work out why successive syncs seemed to be updating the same files - then I realised that my network drive does not support preserving the timestamp of copied files - that and the fact that the clock on the drive was set to the wrong time meant that it was constantly thought that the files on the drive were older than the local files. Now that's sussed it works! All I have to do is fine tune the options and work out how to put it in a cron job and I've got a working sync to my network drive. Thanks again! Neil
Could you explain how you did it. I stopped using Grsync for the same reason. It kept on syncing the same old files over and over again.

---

