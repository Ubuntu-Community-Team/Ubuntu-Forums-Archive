---
title: "Backup recommendations"
date: 2009-07-16
forum: New to Ubuntu
---

### Post by Elep.Repu on 2009-07-16
Sorry, I've been using linux awhile, but I still don't quite understand what a professional would do when backing up their system.
I mean, do you guys just separate /usr /home /etc partitions, and reinstall, and point the mounts to those? Maybe run backintime for a gui rsync option, and then (for gui) grsync to restore (because, am I right, the restore option in backintime doesn't --delete, it only restores?)

I'm using x64 AMD, so the minor options which include Partimage (I don't want to have to boot from a livedisk to back my system up) don't apply to me. Partimage doesn't support 64 bit so.
And it's looking like all the others boot from live disks. 
What's faster?
Is it better to just separate those partitions? What are some tricks with rsync, what am I missing?

I remember a forum post saying "Why would you backup all the root owned data"
I'm not sure what's faster.

And that whole backup concept is hard to understand because of the permissions problem.
Oh yeah, back it all up, and then have to chown it all to use it?
Then there's the question of what to do with the root data if I was backing up that. Can't chown that to myself.
I don't even know what to do. But I do know that I've tried to restore before and it never worked.
I don't want to create images all the time, I would rather do an incremental to save disk usage.

---

### Post by bodyharvester on 2009-07-16
i dont see why you would need to backup your data.

when i used Window$ backups were as common as the system restore feature but linux is much more stable than Window$

what are you planning on doing to your linux that requires you to backup the data? hit it with a sledgehammer? :D

---

### Post by NightwishFan on 2009-07-16
I backup my personal data using a large partition, and rather that store all my data in /home, I link the Document, Music, Picture, and Video folders from my data partition. That way if I reinstall a system, I just wipe my root partition and can have all my data available. For permissions, just run a chown -R on your backup drive to correct them.

/dev/sda1 ext3 /mnt/data
/dev/sda2 swap
/dev/sda3 ext4 /

Choose your partitioning manually at install time to get a setup like this.

If you want to have a runtime backup of root files, then just make sure to backup something before you edit it. A whole system wide backup I am unsure how to do.

---

### Post by Elep.Repu on 2009-07-16
I'm looking for something incremental.
I've done this several times;
 "Oh, let's try this." Then everything is screwed (or whatever)

I understand the separation of data. _Do you run rsync with cron to backup that data_?
_When do you run chown -R, _before installation (and use the same username?) or after?

I've tried simplebackup, which did not work.
I'm really unsure at how the best way to go about it is, _saving time._

Reinstallation is not a rare thing.
I've read about doing the rsync thing manually, but I'm really unsure how to do this (I tried, but this is _very hard_ for me.)

Are there any other separations that should be made other than /usr /etc /~ ?

---

### Post by Elep.Repu on 2009-07-19
Is it better to reinstall and then manually copy it over?
I remember someone saying that it's not "normal" to copy system files in linux. Or it's easier to Not do it.

---

### Post by ratcheer on 2009-07-19
> **bodyharvester said:**
> i dont see why you would need to backup your data.

when i used Window$ backups were as common as the system restore feature but linux is much more stable than Window$

what are you planning on doing to your linux that requires you to backup the data? hit it with a sledgehammer? :D

Apparently, you are one of the extremely lucky ones who have never experienced a hard drive failure. Just wait, your turn will come.

Tim

---

### Post by nmaster on 2009-07-19
this is very good.

 [http://ubuntuforums.org/showthread.php?t=35087&highlight=backup+recovery](http://ubuntuforums.org/showthread.php?t=35087&highlight=backup+recovery)

---

### Post by Elep.Repu on 2009-07-19
> **neal.m.master said:**
> this is very good.

 [http://ubuntuforums.org/showthread.php?t=35087&highlight=backup+recovery](http://ubuntuforums.org/showthread.php?t=35087&highlight=backup+recovery)

Ty neal.m.master for the sym link.

---

### Post by Elep.Repu on 2009-07-20
It's just that it's not incremental, as I've suggested above.
What's the benefit of rerunning a tar command when I can use rsync.
The tutorial was interesting though. 
Has anyone *used* rsync for backup? 
It seems no one ever talks about backing up around here. Or it's just a matter of tarring, which seems archaic in my humble opinion.
What's recreated when it reboots? 
I remember that some part of /var/ was related to applications, and so was recommended for backup. It's for logs though.
Are the only temporary files in /tmp?
Anyone else?

---

