---
title: "Sbackup not backing anything up"
date: 2009-07-01
forum: New to Ubuntu
---

### Post by Benboom on 2009-07-01
I can't figure out how to get sbackup to work. I've installed it with the Synaptic Package Manager and I can set up the options just fine but no matter how I set them after I run the backup when I look at the resulting folder it's empty. I've tried using the default destination and also my home folder, I've tried manual backups and custom backups and the result is the same every time: an empty folder with the backup's date as the name (well a bit more than that for the name, but I'm not on the machine in question now and I don't remember the whole thing).

What obvious thing am I overlooking, please? Running Jaunty on a Fujitsu c2210 laptop.

---

### Post by RealPSL on 2009-07-03
You should post your /etc/sbackup.conf file. You should also check to make sure your target directory for the backup is not full.

---

### Post by TheSoftwareFraud on 2011-10-15
Welcome to "Software development means never having to say you're sorry...or do anything with professionalism".  Ubuntu is slowly sliding the way of Windoze.  Unresponsive developers that unit test and through it over the wall for the public to act as their beta testers.  The pedantic crap you get in these forums is predictable.  Is it a FAT drive?  Are you out of space?  Have you checked the log?

Get real, groids.  10% of EVERY.FREAKING.LAST.PERSON that has installed sbackup over the LAST 7!!! YEARS has had the problem the poster describes.  Verbatim.  The ubiquitous answer?  "Works on my machine!"

This has become a real problem with Ubuntu.  k3b DVD burner constantly enables plug-ins that cause the burn to crash and you can't disable them.  The flash plugin creates as many bugs as it solves every release.  GoogleEarth installs- IF you know the magic package that isn't being checked for but is required (now fixed).

This is no doubt the same.  Some condition that has NOTHING TO DO WITH BACKUP that all the little groids have set on their box and about 10% will just happen to not have done.  sbackup runs and leaves nothing in the backup directly.  No error in the log file on /var.  That's for us to figure out.  Developers can't be bothered.

Bottom line:  For 7 years about 10% of new installs report this bug.  No one has ever proposed a solution or cared.  And brickbats to the 99% of those 10% that finally (accidentally) discovered what the magic condition was and didn't post the result.

"Have you posted your config file?"  What a load of tosh.  Tell me just what is in here (and not obvious from the GUI settings) that would cause it to fail?  Part of the suite of evasive questions developers ask to keep from doing a professional job.

-- the GD config file --

[exclude]
regex = \.mp3,\.avi,\.mpeg,\.mpg,\.mkv,\.ogg,\.ogm,\.tmp,/home/[^/]+?/\.thumbnails/,/home/[^/]+?/\.Trash,/home/[^/]+?/\..+/[c
C]ache,/home/[^/]+?/\.gvfs/
maxsize = 100000000

[places]
prefix = /usr

[dirconfig]
/proc/ = 0
/sys/ = 0
/var/ = 1
/var/cache/ = 0
/tmp/ = 0
/dev/ = 0
/home/ = 1
/bigass/workspace/ = 1
/var/tmp/ = 0
/bigass/programdevelopment/ = 1
/usr/local/ = 1
/etc/ = 1

[general]
stop_if_no_target = 0
target = /bigass/backup
format = 1
purge = log
maxincrement = 21
lockfile = /var/lock/sbackup.lock

---

