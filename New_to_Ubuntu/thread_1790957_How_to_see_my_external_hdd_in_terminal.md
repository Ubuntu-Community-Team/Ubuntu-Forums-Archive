---
title: "How to see my external hdd in terminal"
date: 2011-06-25
forum: New to Ubuntu
---

### Post by lucan on 2011-06-25
hi,
how to read file from a ext hdd using terminal.
i am able to start a terminal, and this is what i get when i try this:
xxxxx-UFF:~$ cd/dev/sdb1
bash: /dev/sdb1: No such file or directory

---

### Post by nzjethro on 2011-06-25
I imagine it's a typo here, but you must include a space between the cd command and your directory. For example:

```
cd /file/path/here
```

As for the error, it's possible that sdb1 isn't mounted. Try:

```
sudo mount /dev/sdb1 /mnt
cd /mnt
```

---

### Post by dcsoldschool53 on 2011-06-25
> **lucan said:**
> hi,
how to read file from a ext hdd using terminal.
i am able to start a terminal, and this is what i get when i try this:
xxxxx-UFF:~$ cd/dev/sdb1
bash: /dev/sdb1: No such file or directory

I maybe a little confused here, but try this first in a terminal```
mount
```This command will tell you what you have mounted to your PC. As I recall, you can not cd to /dev/sdb1. Now, you can connect to what the actual device name or label for /dev/sdb1 is. For example, when I type the mount command I see for /dev/sdd1```
/dev/sdd1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)

```In order for me to cd into this device, I have to use the command```
cd /media/disk
```If the device is call something like "The Monster" or "My Passport", you would type the command like this```
cd /media/My\ Passport
```or```
cd /media/The\ Monster
```There is only one space between \ and Passport and \ and Monster. Sorry for the long explanation.

---

### Post by bdentremont on 2011-06-26
> **lucan said:**
> hi,
how to read file from a ext hdd using terminal...

Nzjethro has you on the right track.  You can not browse into block device in /dev; it is essentially a placeholder which represents a partition, not a directory.  It needs to be mounted first.

_However_, if you are logged into a normal session in Ubuntu Desktop Edition, it will automatically mount most external media to /media when you connect it.  I would look first in /media directory and see if anything there looks like your drive

```

cd /media
ls

```

or look at the list of what is already mounted and where.  I find the disk usage command good for this

```

df -h

```

If you do not see that your drive is mounted, then try exactly what Nzjethro said to mount the device.

---

### Post by lucan on 2011-06-26
hi,
thanks for the reply. i was thinking to keep the story short. i only start using Ubuntu this morning. 

in window, run cmd, all i need to do to get to my ext hdd this something like this:

c:\desktop\user\xxx  h:
H:\

when i read the doc on ubuntu, it say that ext hdd is dev/sdb1 and to change directory is to use cd. that why i thought "cd dev/sdb1" is correct.

---

### Post by Paqman on 2011-06-26
> **lucan said:**
> 
when i read the doc on ubuntu, it say that ext hdd is dev/sdb1 and to change directory is to use cd. that why i thought "cd dev/sdb1" is correct.

In Linux, there's an idea called "everything is a file". So all devices (eg: hard drives, optical drives, as well as software devices like random number generators) show up as a file. So all the stuff in /dev will be the actual devices, but to access the filesystem on that device you go to it's mount point. You can define the mount point as anything you like, but by default things like USB hard drives and flash drives will get automounted in /media when they're plugged in.

---

### Post by dcsoldschool53 on 2011-06-26
> **lucan said:**
> hi,
thanks for the reply. i was thinking to keep the story short. i only start using Ubuntu this morning. 

in window, run cmd, all i need to do to get to my ext hdd this something like this:

c:\desktop\user\xxx  h:
H:\

when i read the doc on ubuntu, it say that ext hdd is dev/sdb1 and to change directory is to use cd. that why i thought "cd dev/sdb1" is correct.

This is the reason why I was confused, I wasn't sure whether you were seeing your device mounted or not. I am glad that it had mounted, and all you needed to do was find the commands to change into that device.
 As Paqman said linux mounts your device automatically as a file in the /media folder. If it is not auto mounting, you always have the fstab file to mount it.

---

