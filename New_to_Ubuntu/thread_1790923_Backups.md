---
title: "Backups"
date: 2011-06-25
forum: New to Ubuntu
---

### Post by john wagner on 2011-06-25
Hi everyone and thanks in advance!

I need to backup my 350gig laptop hard-drive to a 1t stand alone drive.  I am running Ubuntu 10.4 and need to know a simple comprehensive back up program that will do the job (my laptop is full and I plan to install a larger hd-which I allready bought).
Every other back up program I've screwed around with only allows 4gig packs.  That sucks.
Any advice?

---

### Post by dFlyer on 2011-06-25
Deja Dup should do the job without a problem.

---

### Post by Ozymandias_117 on 2011-06-25
Another option would be to just use dd to directly copy the drive wherever you want it.

eg (Assuming /dev/sdb is your drive and you want the backup in ~/backups):```
dd if=/dev/sdb of=~/backups/LaptopDrive.img bs=2048
```

Or a boot CD like clonezilla.

---

### Post by ahears on 2011-06-25
Check out this thread... 'http://ubuntuforums.org/showthread.php?t=35087'.:guitar:You can 'tar' the entire partition and 'untar' it later as one file, and preserve file permissions.



@ Ozymandias Dropbox is not secure. there is a config.db file that allows any user to access your dropbox without your password if they can copy the config.db file.

---

### Post by john wagner on 2011-06-25
> **ahears said:**
> Check out this thread... 'http://ubuntuforums.org/showthread.php?t=35087'.:guitar:You can 'tar' the entire partition and 'untar' it later as one file, and preserve file permissions.



@ Ozymandias Dropbox is not secure. there is a config.db file that allows any user to access your dropbox without your password if they can copy the config.db file.

Didn't Drop Box just get hacked big time?

---

### Post by Ozymandias_117 on 2011-06-25
> **ahears said:**
> Check out this thread... 'http://ubuntuforums.org/showthread.php?t=35087'.:guitar:You can 'tar' the entire partition and 'untar' it later as one file, and preserve file permissions.



@ Ozymandias Dropbox is not secure. there is a config.db file that allows any user to access your dropbox without your password if they can copy the config.db file.

Lol. Nice. I haven't used it in a long time because it only works with Nautilus.  That's really just leftover from like 8 months ago. :D

---

