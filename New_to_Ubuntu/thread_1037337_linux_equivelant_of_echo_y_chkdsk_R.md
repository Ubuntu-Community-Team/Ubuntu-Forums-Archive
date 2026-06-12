---
title: "linux equivelant of echo y| chkdsk /R"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by ant2ne on 2009-01-11
A nice windows script
```
echo y| chkdsk /R
shutdown -r
```
What would I do to get the same results in Ubuntu with ext3 files systems?

---

### Post by blueridgedog on 2009-01-11
Is this designed to trigger the windows disk check upon next boot?

---

### Post by mjheagle8 on 2009-01-11
please explain what this script is supposed to do. 
if it is supposed to check the disk, your computer will automatically do this on every 30 mounts of the drive.

---

### Post by ant2ne on 2009-01-11
> **blueridgedog said:**
> Is this designed to trigger the windows disk check upon next boot?This makes windows flag the disk as dirty, and then reboot to force the checking of the disk. It looks for and recovers bad sectors. As well as making othe FS repairs.

> **mjheagle8 said:**
> please explain what this script is supposed to do. 
if it is supposed to check the disk, your computer will automatically do this on every 30 mounts of the drive.Sometimes I don't want to wait for 30 boots. Particularly if I use hibernation/syspend more frequently than boots. I want to flag the disk and perform the check, NOW. 

FS problems can cause all kinds of errors. Part of my troubleshooting; I like to rule out FS problems before looking at other possible causes.

---

### Post by mjheagle8 on 2009-01-11
ok, so you want to force a fsck. this article describes how to do that.
[http://www.cyberciti.biz/faq/linux-force-fsck-on-the-next-reboot-or-boot-sequence/](http://www.cyberciti.biz/faq/linux-force-fsck-on-the-next-reboot-or-boot-sequence/)

---

### Post by mjheagle8 on 2009-01-11
you'd use this command in the terminal. or you can make a script or launcher to execute it.
> Frce fsck on next boot using shutdown command

The -F option force fsck on reboot, login as root and type the following command to reboot and run fsck:
```
# shutdown -rF now
```


---

### Post by ant2ne on 2009-10-10
> **mjheagle8 said:**
> you'd use this command in the terminal. or you can make a script or launcher to execute it.This does not seem to work in ubuntu. 

This does

sudo touch /forcefsck

---

### Post by ant2ne on 2009-11-12
so, after I do a sudo touch /forcefsck, where do I find the results of that scan?

---

### Post by ant2ne on 2010-04-16
bump - I would still like to see the log of this scan.

---

### Post by lisati on 2010-04-16
> **ant2ne said:**
> bump - I would still like to see the log of this scan.

The scan will occur the next time you boot. I would suggest looking in your system logs.

---

### Post by Didius Falco on 2010-04-16
Check in 

```
/var/log/fsck
```

Mine reports > (Nothing has been logged yet.), which leads me to believe it will only make a log entry if there are errors. Fortunately, I've never run into that problem - knock wood!

---

