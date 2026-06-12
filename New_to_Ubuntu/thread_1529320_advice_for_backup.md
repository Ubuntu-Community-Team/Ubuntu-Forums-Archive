---
title: "advice for backup"
date: 2010-07-12
forum: New to Ubuntu
---

### Post by nnjond on 2010-07-12
Hi,

$ chmod 777 /home/nnjond/*

returns a load of

chmod: changing permissions of ...

 Operation not permitted

how can i free up these files?

Thanks

---

### Post by hellarough on 2010-07-12
I  dont think you want to chmod your entire home directory like that, I did that once and caused a plethora of errors. 

Most notable was this problem [$HOME/.dmrc]("http://ubuntuforums.org/showthread.php?t=371052&page=7")

Anyways, if you are looking to backup your home directory I suggest you look into using rsync.

---

### Post by nnjond on 2010-07-12
Thanks for your interest.

I'm trying to rsync from one ~/home on hdd a, to ~/home hdd b, using a live cd, but it returns a load of; eg:

rsync: opendir "/media/a2ab9331-effd-4855-8e0a-6c7f1a9d63b5/home/nnjond/.Skype" failed: Permission denied (13)

---

### Post by hellarough on 2010-07-12
Please post the exact command you were tring to run so we can further troubleshoot the problem. Right now, my guess is that command doesnt have the correct switches/options for the type of backup you are trying to perform ie. you might be attempting to preserve permissions on the backup when you shouldnt, forgetting to preserve directory structure, or something like that.

---

### Post by Paqman on 2010-07-12
> **nnjond said:**
> 
I'm trying to rsync from one ~/home on hdd a, to ~/home hdd b, using a live cd, but it returns a load of; eg:


Instead of modifying all the permissions in your home folder, just run rsync as root. That means using sudo if you're on the command line, or if you're using grsync, to launch it with the command: gksu grsync.

---

### Post by mike555 on 2010-07-12
Why not just get "Luck Backup " and let it do the work.

---

