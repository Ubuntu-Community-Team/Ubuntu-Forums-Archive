---
title: "Toshiba External HD Virtual CD"
date: 2010-06-12
forum: New to Ubuntu
---

### Post by Tumpster on 2010-06-12
Hey there, I'm looking to remove this stupid program/software. I've opened it up in all the partitioning programs and it isn't seen by them. It only takes up 42.5mb of space but yet it still fires up everytime I'm utilzing the drive, I'd like to just format it and then use it as my main backup drive. Here is the link that I've been looking over but yet its been frustrating:
[http://www.techsupportforum.com/hardware-support/hard-drive-support/440393-virtual-cd-removal-toshiba-1tb-ext-hdd.html](http://www.techsupportforum.com/hardware-support/hard-drive-support/440393-virtual-cd-removal-toshiba-1tb-ext-hdd.html)

I could use any help!

---

### Post by Tumpster on 2010-06-13
> **Tumpster said:**
> Hey there, I'm looking to remove this stupid program/software. I've opened it up in all the partitioning programs and it isn't seen by them. It only takes up 42.5mb of space but yet it still fires up everytime I'm utilzing the drive, I'd like to just format it and then use it as my main backup drive. Here is the link that I've been looking over but yet its been frustrating:
[http://www.techsupportforum.com/hardware-support/hard-drive-support/440393-virtual-cd-removal-toshiba-1tb-ext-hdd.html](http://www.techsupportforum.com/hardware-support/hard-drive-support/440393-virtual-cd-removal-toshiba-1tb-ext-hdd.html)

I could use any help!

Anybody? I would even take a solution to stop the Virtual CD from coming up.

---

### Post by anewguy on 2010-06-13
My brother in-law has a Toshiba external USB drive something like 640 gig.  I've seen the partition that comes up as the virtual cd driver and starts the backup software, but never tried to remove it.  I always just thought something like gparted would remove it.

Something else you may need to be aware of with the drive:

Some of these drives completely power off on their own after a (unknown to me) amount of time.  The only way to get them back is to press the power button again.  If you plan to have automatic backups (I have my brother in-laws scheduled for the middle of the night), this auto-shutoff causes the backups to fail as the drive is not there.  Toshiba did put out a patch for this in March so that the drive follows the PC, but I haven't installed it to my brother in-laws drive yet.  His PC goes to sleep but wakes up because of the scheduled backup - I don't know if the drive would wake up in time to be seen for the backup.

Dave ;)

---

### Post by Tumpster on 2010-06-14
> **anewguy said:**
> My brother in-law has a Toshiba external USB drive something like 640 gig.  I've seen the partition that comes up as the virtual cd driver and starts the backup software, but never tried to remove it.  I always just thought something like gparted would remove it.

Something else you may need to be aware of with the drive:

Some of these drives completely power off on their own after a (unknown to me) amount of time.  The only way to get them back is to press the power button again.  If you plan to have automatic backups (I have my brother in-laws scheduled for the middle of the night), this auto-shutoff causes the backups to fail as the drive is not there.  Toshiba did put out a patch for this in March so that the drive follows the PC, but I haven't installed it to my brother in-laws drive yet.  His PC goes to sleep but wakes up because of the scheduled backup - I don't know if the drive would wake up in time to be seen for the backup.

Dave ;)

Yes, I've rocked both and in the windows boot it does not work. It says no Toshiba drive found after I formated it.

---

### Post by anewguy on 2010-07-09
Found this on Toshiba's support site:

[http://http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/bulletin.jsp?ct=SB&soid=2640271&ref=EV]("http://http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/bulletin.jsp?ct=SB&soid=2640271&ref=EV")

Dave ;)

---

