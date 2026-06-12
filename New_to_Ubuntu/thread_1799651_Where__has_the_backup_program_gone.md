---
title: "Where  has the backup program gone"
date: 2011-07-07
forum: New to Ubuntu
---

### Post by bobmac on 2011-07-07
Folks,

I used the Ubuntu Software Centre to install 'Simple Backup and Restore', however, after it is apparently installed it doesn't appear under any of the Applications menus.

Can somebody let me know where it is and how to get it into the Applications menus

Many thanks,

Bob

---

### Post by wolfen69 on 2011-07-07
```
sudo apt-get install sbackup-gtk
```

edit: go to main menu and see if you can put it in there. And sometimes logging out and back in can do it.

---

### Post by bobmac on 2011-07-07
Wikfeb69
Tried your suggestions the sudo... seemed to work but nothing appears in the menus. Being a beginnerk, I can't figure out how to get the app into the main menu.

Regards,

Bob

---

### Post by kalimojo on 2011-07-07
> **wolfen69 said:**
> ```
sudo apt-get install sbackup-gtk
```edit: go to main menu and see if you can put it in there. And sometimes logging out and back in can do it.

i installed sbackup-gtk . it doesnt support backing up to removeable media it seems.

---

### Post by bobmac on 2011-07-07
Folks,

If I can't get sbackup to work have you any suggestions for a backup/restore program that I can use to backup to an external drive.

Regards,

Bob

---

### Post by mikodo on 2011-07-08
Hi,

After I found Sbackup not working for me anymore, I searched around for any different GUI backup solutions that I would like as much as I did with Sbackup and found Deja-dup, and have been using it now for ~ a year or so and like it a lot. Like you I use it to back up to an external HD. (My /home). Deja Dup is a featured app in ubuntu's Software Center and can be installed from there.

Deja-Dup in Launchpad:

[https://launchpad.net/deja-dup](https://launchpad.net/deja-dup)

One of many sites writing about Deja-Dup:

[http://www.makeuseof.com/tag/dj-dup-perfect-linux-backup-software/](http://www.makeuseof.com/tag/dj-dup-perfect-linux-backup-software/)

And according to this link; OMG Ubuntu site, Deja-dup might be the default backup app in Ubuntu 11.10:

[http://www.omgubuntu.co.uk/2011/05/deja-dup-backup-tool-proposed-for-default-in-ubuntu-11-10/](http://www.omgubuntu.co.uk/2011/05/deja-dup-backup-tool-proposed-for-default-in-ubuntu-11-10/) 

Have a look at it, as it is refreshingly easy to use.

:)

---

### Post by Jacobonbuntu on 2011-07-08
> **bobmac said:**
> Folks,

If I can't get sbackup to work have you any suggestions for a backup/restore program that I can use to backup to an external drive.

Regards,

Bob

I use rsync/grsync, Grsync has an easy to use GUI and works solid and fast. If you want to make scheduled backups you can just copy the output of the Rsync -output window and paste it in gnome-schedule. Sounds a bit complicated, but is quite simple and it works perfectly.

Before, I tried almost all other "easy" backup solutions, but they all failed to me or worked slowly.

*edit: if you'd like to try this I can give you a more detailed description on how to.*

---

### Post by RayArdia on 2011-10-05
I tried Deja-dup, all seemed to go OK but at end of backup I got this error message

BackendException: Could not copy /tmp/duplicity-ju3LHU-tempdir/mktemp-2Y46Nl-2 to /media/Philips External Hard Disk/duplicity-full.20111005T142057Z.vol1.difftar.gpg

What am I doing wrong please?
Ray

---

### Post by verymadpip on 2011-10-05
Sorry didn't see the SOLVED

---

### Post by kurt18947 on 2011-10-05
Rsync is installed by default at least in 11.10.  I added Grsync so I have a GUI.  I wanted to synchronize two folders and don't see a way to accomplish that but it's easy enough to create two sessions.  One backs up A to B, the other backs up B to A.  I also was annoyed that by default it copies over the folder with files in it.  I soon found out that adding a forward / to the end of the path it just copied files without copying the containing folder which is what I wanted.

I did find a java app which is sort of interesting and does work in 11.10. It's called DirSyncPro(DirSyncPro.org), is licensed under GPL3 and is a java app which claims to be platform independent.  The trick to finding removable media appears to be that except in Grsync, I needed to look in /home/user/media which was the USB drive mount point.  The USB hard drive I was using showed up there.  I'm inclined to stick with Grsync just because it's well proven, the GUI makes it easy to use and seems to do what I need it to do.  

Either of these applications will back up data files.  If you want to back up an entire installation, OS and all,  you might want an imaging program.  Clonezilla is frequently mentioned for that purpose.

---

