---
title: "[SOLVED] What is the mount point for cameras?"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by rbc on 2008-12-10
I connect my digital camera, f-stop takes over, imports the pictures. Beautiful, no problem, but where does the device actually get mounted? I am sure there’s a very simple answer, but I am tired and I simply cannot figure this out.

---

### Post by Paqman on 2008-12-10
Cameras work just like all removable storage. They all get mounted at /media, which is why they show up on the desktop.

---

### Post by Titan8990 on 2008-12-10
You should try the mount command. It gives a list of all the mounted drives and their mount locations:

```
jordan@einstein:~$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sdb1 on /media/backup type ext3 (rw)

```

---

### Post by rbc on 2008-12-10
Yes. I figured that it ought to be mounted under /media because, as you pointed out, it is being displayed on the desktop, but it is not showing up in /media. Nor does the output of the "mount" command change at all after inserting the USB cable. Hence my confusion

---

### Post by Michael.Godawski on 2008-12-10
Perhaps reading through this thread will shed some light on this issue:

[LIST]
[*][http://ubuntuforums.org/showthread.php?t=947695](http://ubuntuforums.org/showthread.php?t=947695)
[/LIST]
Basically it says that some cameras are not mounted in /media because they use a PTP Protocol.

[LIST]
[*][http://en.wikipedia.org/wiki/Picture_Transfer_Protocol](http://en.wikipedia.org/wiki/Picture_Transfer_Protocol)
[/LIST]

---

### Post by philinux on 2008-12-10
> **rbc said:**
> Yes. I figured that it ought to be mounted under /media because, as you pointed out, it is being displayed on the desktop, but it is not showing up in /media. Nor does the output of the "mount" command change at all after inserting the USB cable. Hence my confusion

It should be under places.

---

### Post by mc4man on 2008-12-10
I believe in 8.10 (intrepid) you'll find it in .gvfs (home directory

---

### Post by rbc on 2008-12-10
Ahh, Wikipedia. The one place I didn't look. Thank you Michael.Godawski. That explanation helped a lot. And mc4man, I do have Intrepid and it is, in fact, in .gvfs. Thank you

---

### Post by mc4man on 2008-12-10
What's also a little different (8.10 vs. 8.04) is that if you want to import to some other apps like gthumb you need to umount the camera first. (at least with ones that use PTP

For my canon I've set gthumb up as a default choice, but set the action to do nothing.

Then in computer after it mounts I r. click - unmount, and then r. click - open with gthumb on the canon icon.

In 8.04 it never 'mounted' so I could set gthumb to auto open

---

