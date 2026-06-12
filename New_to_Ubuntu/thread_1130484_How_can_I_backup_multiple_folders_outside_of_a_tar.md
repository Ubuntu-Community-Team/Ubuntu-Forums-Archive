---
title: "How can I backup multiple folders outside of a tar script directory?"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by davidstri on 2009-04-19
I have a tar script that I want to use to backup multiple folders in my home directory. The tar script is inside of a folder called cron_scripts in my home directory. So to backup the multiple folders in my home directory I would have to use something like this
```
tar -czpf backup.tar.gz * /fileoutsideofscriptdirectory * /fileoutside
```
, but for some reason it only backs up the first file and then says "/fileoutside: Cannot stat: No such file or directory". 
Help.

---

### Post by Gen2ly on 2009-04-19
I think your choosing * is confusing tar.  You can use * but it will choose everything in the current directory.  Plus naming the backup before giving the options has always worked better for me.

---

### Post by steve101101 on 2009-04-19
here is my command for backup my entire system:

```

tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /

```

here is also a thread that may help [http://ubuntuforums.org/showthread.php?t=1126559]("http://ubuntuforums.org/showthread.php?t=1126559")

---

### Post by davidstri on 2009-04-20
Steve: I guess instead of choosing all the files in my home directory, I could exclude the files(which include all the hidden files) I don't want backed up with --exclude=/.* (to get rid of all the hidden files in my home folder).
Maybe that would work...

---

### Post by davidstri on 2009-04-20
Thank you for your help, you gave me a good idea and this is what I found. [http://ubuntuforums.org/showthread.php?t=55254](http://ubuntuforums.org/showthread.php?t=55254) 
I guess this thread has been solved.

---

