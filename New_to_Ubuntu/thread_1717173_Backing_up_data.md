---
title: "Backing up data"
date: 2011-03-29
forum: New to Ubuntu
---

### Post by Torp3x on 2011-03-29
Ok so I've seen that there are a few backup applications out there, firstly, can anyone recommend one? The type of backup I'd like to do is one which will enable me to roll back my system to a previous state if anything goes wrong, much like Windows system restore.

Secondly, is it at all possible to backup my data from this laptop, and restore that data to another, identical laptop? I don't just mean my folders and files, I mean all the system settings too; the drivers, compiz settings, etc etc....?

---

### Post by nhwd on 2011-03-29
never mind

---

### Post by Rubi1200 on 2011-03-29
Here is some more information to digest:
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

How and what you backup really depends on your needs.

---

### Post by Torp3x on 2011-03-29
Thanks. I've read through a fair bit of documentation, just wondered if there was a particular stand-out app suited to this kind of thing.

So is there nothing, in theory, that will stop me from transferring the backup files or folder from this laptop to another (identical) machine, then installing and running the backup application on that machine to restore from the transferred backup file?

I know you can do this with mobile phones, just wondered if it was possible on Ubuntu.

---

### Post by Rubi1200 on 2011-03-29
I think this post describes another way to do what you want:
[http://ubuntuforums.org/showpost.php?p=10614963&postcount=2](http://ubuntuforums.org/showpost.php?p=10614963&postcount=2)
[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by vanadium on 2011-03-29
You better invest in a good, frequent backup routine for your user data. These are irreplaceable. Operating systems, in contrast, come for free and install in less than one hour.

Backing up your entire system is a tedious thing to do. you will not do it every day. The day you want to restore an old backup, you will notice how outdated the system is you are restoring. And the restore won't take a lot less time than a new install.

For backing up my user data, I use rsync

rsync -av --delete ~/Documents /media/Drive/Documents

This creates a mirror copy of your data. First time, the copy is at normal speed. Next time, only changed files are copied, and the backup takes 15 seconds. Something you easily can do once a day or even more.

---

