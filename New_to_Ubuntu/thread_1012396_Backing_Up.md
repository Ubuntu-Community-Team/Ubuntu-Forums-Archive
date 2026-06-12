---
title: "Backing Up?"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by camRW on 2008-12-15
What would be the easiest method for backing up 80 gig hard drive to an external 250 gig hard drive?

I only have 8 gigs free, otherwise I would have done this method:
tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /

Should I just create the tar on the harddrive? It seems like that would take FOREVER (not sure how long, 5 hours? longer?)

Any input appreciated.

---

### Post by louistan3 on 2008-12-15
do you need a backup of the files? or kinda like an image?

for images, i use a program called Boot It NG. Not sure where to get it though cause someone just sent it to me. lol

---

### Post by jerome1232 on 2008-12-15
This really depends on what you plan on doing with the backup?

If you want to make an exact copy of the hard drive that can be slapped back in and you have a working system I would image the drive. You can use dd or partimage for this.

If you are just wanting to backup your personal files and such I would use rsync or tar, or simply copy the files using cp or via nautilus.

Let us know exactly what you're wanting to backup and/or the purpose of the backup and we can give you the best backup method.

---

### Post by starcannon on 2008-12-15
Sbackup is a nice utility with a GUI
[http://onlyubuntu.blogspot.com/2007/03/backup-and-restore-ubuntu-system-using.html](http://onlyubuntu.blogspot.com/2007/03/backup-and-restore-ubuntu-system-using.html)

dd as mentioned is also very nice:
**[Creating disc images using dd]("https://help.ubuntu.com/community/BackupYourSystem#From%20the%20command%20line")**

GL and have fun

---

