---
title: "tar exits with error"
date: 2009-11-19
forum: New to Ubuntu
---

### Post by Buuntu on 2009-11-19
I am trying to learn of several ways to perform backups on my ubuntu machine, at least on my /home folder.  I've had luck before with 'cp' but 'tar' is giving me errors when I try to use it to create a more compressed version of my /home folder.  This is what my terminal looks like:
```
$ sudo su
# tar -cvpfz /media/AE45-AAA0/HomeBackupNov1909.tar.gz /home
blah
blah
blah
etc...
/home/gabriel/.VirtualBox/HardDisks/Windows.vdi
tar: z: Wrote only 4095 of 10240 bytes
tar: Error is not recoverable: exiting now

```So I thought that the Windows.vdi might be too big for tar to handle but after --excluding it it just got stuck on an mp4 file.  I'm not sure what's causing the problem and would like to know if any of you have a solution.

Thanks

---

### Post by Locke_99GS on 2009-11-19
Try this

```
$
tar -czf /media/AE45-AAA0/HomeBackupNov1909.tar.gz /home

```

---

### Post by snova on 2009-11-20
> **Buuntu said:**
> So I thought that the Windows.vdi might be too big for tar to handle but after --excluding it it just got stock on an mp4 file.  I'm not sure what's causing the problem and would like to know if any of you have a solution.

Just an idea, but what filesystem does the target drive use? Maybe the archive exceeds the maximum file size (as may be the case with FAT).

---

### Post by scorp123 on 2009-11-20
> **Buuntu said:**
> I am trying to learn of several ways to perform backups on my ubuntu machine ... 

"How to backup your stuff UNIX-style"
[http://forums.linuxmint.com/viewtopic.php?f=42&t=3969&start=0&st=0&sk=t&sd=a](http://forums.linuxmint.com/viewtopic.php?f=42&t=3969&start=0&st=0&sk=t&sd=a)

---

### Post by Buuntu on 2009-11-20
> **Locke_99GS said:**
> Try this

```
$
tar -czf /media/AE45-AAA0/HomeBackupNov1909.tar.gz /home

```

Thanks, that seems to have worked.  However I still have a problem and I think it has to do with the drive being formatted in fat32.  It's not letting me store a huge tar file, probably because fat32 has a 4 GB limit.  I can reformat the drive but I don't know what the best format would be.  EXT3/4 would be fine except that then I can't access it on Windows or Mac machines.  The other obvious choice would be NTFS, but GParted isn't letting me choose that (I don't think it's supposed to).  Do I even have to format to use the drive as a storage device or can I use it unformatted?  If not, how can I format it to NTFS?

Also, I'm guessing the previous error was with trying to keep file permissions with -p, but could you explain why it gave me that error when I gave it that option?  I would like to know in the future, so I can diagnose similar problems myself.

---

### Post by Locke_99GS on 2009-11-20
You shouldn't need to use -p when creating packages, but it shouldn't cause you any issue either. I believe your issue stemmed from having -z be the last option, when it should have been -f. -f requires an argument, which will be immediately following it. You had "z" immediately following -f, which still function on my machine when testing but is improper use of opts. It could confuse the option parser within tar, which I believe is what happened.

---

### Post by Buuntu on 2009-11-20
Ahhh, that would explain why the file it created was called 'z', hahaha.  Thanks so much! ^^

---

