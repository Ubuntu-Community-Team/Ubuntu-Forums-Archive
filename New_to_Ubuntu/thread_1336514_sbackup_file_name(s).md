---
title: "sbackup file name(s?)"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by BobJam on 2009-11-24
I used the Simple Backup (sbackup) utility to try to backup my /home partition.

I didn't realize how big my /home directory was (should have checked it before I started), because even with compression (which I assume sbackup does, though I couldn't find any settings for this in the sbackup GUI) when I rebooted I got a warning that my / was dangerously full.  I took a look at the / partition in gparted, and where I had before had over 17GB of free space in that partition I now had just a sliver of free space (the warning advised that I only had some 270MB of free space left in /)

So I popped in my System Rescue CD and enlarged the / partition (fortunately I had plenty of free space on my HDD to work with).  The warning is gone now, but I'd like to find that backup file(s) that sbackup made (and maybe delete it, and go back to the old manual tar method I was using before sbackup - [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087) ).  In any case, I'd like to look at what it did.

I searched on the date I did it, in the destination directory I gave sbackup, but couldn't find what would look like backup files.

So, assuming it put this (these?) things where I told it to put them (it?), what would be the file name(s?) that sbackup made, or the subfolder it stored them/it in, that I can look for?

---

### Post by oldfred on 2009-11-24
I have used sbackup. I created a separate partition just for the backups and this is what is there. They are set to root and in Nautilus shows 0 size. When my original backup was to a FAT32 it was always 4 GB. Little did I realize until years later that that was the FAT limit and I only had a partial backup.

/home/fred/backup/2009-08-26_19.45.18.619167.ubuntuDuo.ful

---

### Post by dixonstalbert on 2009-11-24
hello

sbackup creates a big compressed file called files.tgz and puts it in a folder named *todaysdate.time.?randomnumber.computername.*and ending in either "inc" if it is incremental or "ful" if it is a full backup.

a common problem with sbackup is when you are backing up to an external drive and the mountpoint has changed from the first time you ran sbackup.

If this happens,sbackup will create a new folder under /media with old mountpoint name and put files.tgz in there. Even though it is under /media directory, it is still part of the root directory systen and it will eat up all all your free space.

the newer versions of sbackup address this problem and there is a checkbox option in sbackup config where you can elect to not backup if the backup directory is not present.

---

### Post by BobJam on 2009-11-25
> **oldfred said:**
> They are set to root and in Nautilus shows 0 size.I am sure that I set the destination as my home directory, but I found a "backup" folder in /var, which is apparently the default for sbackup.

It was indeed "0", and had no contents, but I had to do gksudo nautilus to view it (that is, open the folder and view that it had no contents).

And then the next problem I had was deleting it permanently.  It went to the trash, but when I went to view the trash (as superuser, of course), I got a message that the "Operation not supported":

[IMG]http://i47.tinypic.com/ndu2r9.jpg[/IMG] 

I was sudo, so I couldn't figure this out   (BTW, I do indeed have nautilus set to show hidden files, so that wasn't it either) . . . but for some reason I couldn't view, and consequently delete permanently, the contents of the root trash.  I Googled, and found this link:  [http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

That solved my problem, and when I permanently deleted the contents of the root Trash (it was full of deletions BTW), including the /var/backup folder, my / returned to the 4.1GB that it had been before I used sbackup (and had all that crappola in my root trash).

> **oldfred said:**
> /home/fred/backup/ 2009-08-26_19.45.18.619167.ubuntuDuo.fulNever did find any .ful or .inc backup file, but deleting that /var/backup folder apparently did it anyway.

> **dixonstalbert said:**
> sbackup creates a big compressed file called files.tgz and puts it in a folder named todaysdate.time.?randomnumber.computername.and ending in either "inc" if it is incremental or "ful" if it is a full backup.See above.  I never found that .tgz file, nor the .ful or .inc folder.  (Do you have that backwards?).  I'm tempted to try sbackup again just to see if I can find (and it creates) those files/folders.

> **dixonstalbert said:**
> a common problem with sbackup is when you are backing up to an external drive and the mountpoint has changed from the first time you ran sbackup.I wasn't backing up to an external drive.

I'm thinking that sbackup is really just a GUI front end to that manual tar method I linked to in my original post . . . is it?

---

### Post by oldfred on 2009-11-25
It is a python/glade program that just runs tar.

See
/usr/share/sbackup  sbackupd.py is the actual backup all the other python programs are setup and configure.

---

### Post by BobJam on 2009-11-25
Kewl . . . thanks.

---

