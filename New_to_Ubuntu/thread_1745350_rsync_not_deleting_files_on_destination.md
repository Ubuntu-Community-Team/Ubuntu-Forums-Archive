---
title: "rsync not deleting files on destination"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by exup1000 on 2011-04-30
I am running a bash script to synchronise files on a number of comptuers, but for some reason the files on my PC which I perform the back up from does not mirror the home directory. All the other files are being mirrored on my PC and the other workstations correctly. That is an old source file is delete and when the back up runs again the old file is deleted from the backup. Note also using -a (archive does not make a difference) neither does using --delete
I have also tried running the bash script as the user and as root.
The destination drive is simply a removable drive on the same PC.

The code that I was running was
```
rsync -rt --progress --del -vv /home/ /media/Backup1/TESTW100/home/
```

Where as if I specifically nominated folders it seems to work
```
rsync -rt --progress --del -vv /home/au009900/Documents/ /media/Backup1/TESTW100/home/au009900/Documents/
		rsync -rt --progress --del -vv /home/au009900/Desktop/ /media/Backup1/TESTW100/home/au009900/Desktop/
		rsync -rt --progress --del -vv /home/au009900/Downloads/ /media/Backup1/TESTW100/home/au009900/Downloads/
		rsync -rt --progress --del -vv /home/au009900/Music/ /media/Backup1/TESTW100/home/au009900/Music/
		rsync -rt --progress --del -vv /home/au009900/Desktop/ /media/Backup1/TESTW100/home/au009900/Picutres/
		rsync -rt --progress --del -vv /home/au009900/Videos/ /media/Backup1/TESTW100/home/au009900/Videos/
```

I dont want to manually type in every folder so can you let me know what I am missing. Like I say it seems to be unique to the home folder only.

---

### Post by rotwang888 on 2012-01-16
Howdy.  I know this is ancient, and I hope you've solved the problem by now, but I thought I'd post the solution that worked for me.  Rsync worked as expected for backing up everything but my home directory from which nothing was ever deleted.  Anyway, I dug up the following...
> If the sending side detects any I/O errors, then the deletion of any files at the destination will be automatically disabled. This is to prevent temporary filesystem fail&#8208;
ures (such as NFS errors) on the sending side from causing a massive deletion of files on the destination. You can override this with the --ignore-errors option.

With --ignore-errors added the old files in my home were finally deleted.  I think this is because I always would have at least one error from a Firefox temp file or some such that had vanished while rsync was running.  I hope this helps someone- this was driving me nuts for a while.

---

### Post by mammothFoot on 2013-01-22
Wow, thanks a lot, that was really helpfull. I was starting to get crazy with this bug !

---

### Post by Obi-Wan-YJ on 2013-07-01
Wow.  I've been using rsync for many, many years to backup my system.  Just this past weekend, after having to restore my /home filesystem from one of my two backup drives (they alternate living off-site), I noticed that one of my backup drives contained many more files than did the other one.  Many of the extras were in /usr, and pre-dated a complete OS wipe & re-install I'd done six months ago.  I wonder how long this refusal to delete files has been going on.  I really wish I'd discovered it before I restored /home.  I really wonder how many unwanted files have now returned.  It's not uncommon for me to move entire directories around.  I'm scared that I now have both copies of those dirs.  <sigh>

Anyway, thanks for posting this solution.  --ignore-errors worked like a charm.  The first time I ran rsync with that option, it deleted 421,140 files from my backup drive.  <shudder>

---

### Post by oldos2er on 2013-07-02
Old thread closed.

---

