---
title: "Complete Automated system backup"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by steve101101 on 2009-04-15
I want to backup everything from my primary hard drive, which is 500GB to a secondary hard drive which is the same capacity on a weekly basis. I want to not only back up my data, but my system files as well so if my first hard drive died the second would would be able to run immediately. 

I would like this automated so that its easy and convenient. 

Does anyone know how to do this. I have seen sbackup but don't know how to backup everything.

Thanks in advance.

---

### Post by BDNiner on 2009-04-15
You can try cloning software (like ghost or arconis) that i feel would make the replacement hard drive plug and play. All other kinds of backup solutions would require you to setup partitions and grub. Cloning though it harder to automate

---

### Post by nandemonai on 2009-04-15
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem) is a good place to start.

You could automate with a cron job.

---

### Post by steve101101 on 2009-04-15
whats a cron job?

---

### Post by ubuser_7 on 2009-04-15
Give Backuppc a shot
[http://backuppc.sourceforge.net/](http://backuppc.sourceforge.net/)

I allows you to take incremental and complete backups and browse the files too. Its extremely configurable and reliable!

---

### Post by prem1er on 2009-04-15
> **steve101101 said:**
> whats a cron job?

You can schedule a command execution.

[http://troy.jdmz.net/cron/]("http://troy.jdmz.net/cron/")

---

### Post by steve101101 on 2009-04-15
right now I run the command ... ```
 tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys / 
```

this creates a tar that is a complete backup. so i could do a cron to automate this?

---

### Post by sgosnell on 2009-04-15
Yes.  Or you could use remastersys, which gives you a bootable install .iso, and use a cron job to run that.  It does require root access, so you'll need to read the man pages for it.

---

### Post by steve101101 on 2009-04-15
okay thanks

---

### Post by steve101101 on 2009-04-16
cron is amazing. i am just fiddling with it and have already been able to run a script that completes a simple tasks and then rights to a log saying it was successfully done and time stamps it. cron is very powerful and pretty easy to use.

---

