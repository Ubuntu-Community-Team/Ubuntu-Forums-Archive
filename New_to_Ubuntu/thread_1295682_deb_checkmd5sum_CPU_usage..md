---
title: "deb_checkmd5sum CPU usage."
date: 2009-10-19
forum: New to Ubuntu
---

### Post by Zenmij on 2009-10-19
I can't seem to find any information on what this is, but every so often my CPU usage goes through the roof. I see from conky, its deb_checkmd5sum.

Any information would be helpful.

---

### Post by martrn on 2009-10-19
Its a kernel message.  It might be a segmentation fault, A suppression of something happening inside the kernel (eg a kernel module prevented from loading), a badly behavior of one application.  The checkmd5sum is only telling you that something is wrong not exactly what is wrong, but you know that anyway.  EG, check md5sum + reload.  It seems low level, could be anything though.

---

### Post by Zenmij on 2009-10-20
After some research I managed to sort it out. There was a cronjob for something called John the Ripper running on my system - so I just deleted the cronjob.

Unsure how this got on my PC though as I hadn't installed it.

---

### Post by Fogginz on 2009-10-20
=)

---

### Post by Zenmij on 2009-10-20
Ah well, I thought it had - but its still running. Starts up about 1am.

Can anyone shed any light on this for me? What logs to check or where to look to see if its a scheduled task?

Thanks very much.

---

### Post by Zenmij on 2009-10-20
Quick update. May be due to tiger it caused huge numbers of deb_checkmd5sums to run almost broke me... almost.

---

### Post by pabloab777 on 2010-08-09
Same problem here, is Tiger*. I found it with htop. There is a better way to detect who is accessing too much to hdd (not cpu%)?
Sometimes mlocate, sometimes auth-for-gdm... :S


* Tiger is  a package consisting of Bourne Shell scripts, C code and data files which is used for checking for security problems on a UNIX system.  It scans system configuration files, file systems, and user configuration files for possible security problems and reports them.  The command  tigexp(8) can be used to obtain explanations of the problems reported by tiger.

---

### Post by Ozymandias_117 on 2010-08-09
> **Zenmij said:**
> After some research I managed to sort it out. There was a cronjob for something called John the Ripper running on my system - so I just deleted the cronjob.

Unsure how this got on my PC though as I hadn't installed it.

John the Ripper is a program to crack users passwords.

---

### Post by d3v1150m471c on 2011-03-31
if you don't know how it got there or why it's on cronjob it's probably a good idea to wipe your data and reinstall

---

### Post by davidsarah on 2012-10-02
This is yet another case of Ubuntu enabling obnoxiously CPU-hogging processes of dubious usefulness by default.

Just do:
sudo dpkg -P tiger
sudo pkill -9 deb_checkmd5sum

---

### Post by overdrank on 2012-10-02
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

