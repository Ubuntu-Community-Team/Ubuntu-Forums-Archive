---
title: "Backup"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by meddyliol on 2009-01-16
Hi, I have just installed Ubuntu 8.04 and am in the process of downloading various packages. When I have the system more or less the way that I want, is there a facility available to do a backup? either of the complete system or parts of?

Cheers

Brian :guitar:

---

### Post by nhasian on 2009-01-16
i like to use simple backup.  its easy to use.

```
sudo apt-get install sbackup
```

---

### Post by Zack McCool on 2009-01-16
You may wish to search the forums rather than starting a new thread on it.  As you might imagine, this is a frequent question, and the short answer is YES! There are several different ways you can effectively back up your system.

I use a much different way than the next guy might.  You might want something with a GUI interface, whereas I like mine to be done from a shell script, run from cron (the system's scheduler).  I back up to disk across my LAN, you might want to use a tape or a DVD.  

Some things you might want to look into: rsnapshot, rsync, sbackup, tar

---

### Post by meddyliol on 2009-01-16
Thanks a lot. By the way where is the Thanks Button? Sorry for being so stupid. 

Cheers

Brian :D

---

### Post by hyper_ch on 2009-01-16
you have to decide if you wnt to create a backup image or make backups file by file...

---

