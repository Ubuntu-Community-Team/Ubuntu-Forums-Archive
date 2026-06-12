---
title: "How to mount ext4 permanently"
date: 2010-01-18
forum: New to Ubuntu
---

### Post by Sejanus on 2010-01-18
How can I mount ext4 partition permanently? Currently it gets mounted only when I go to, i.e., Places -> MyExt4Partition. Thanks in advance!

---

### Post by Grenage on 2010-01-18
Take a look at /etc/fstab - it controls what automatically mounts at boot time.  You'll need elevated right to modify it:

```
sudo vim /etc/fstab
```
or
```
gksu gedit /etc/fstab
```

You'll then need to add a line like:

```
/dev/sdb1       /mnt/archive    ext4   defaults  1  2
```

Where sdb1 is the partition you want to mount, and /mnt/archive is the mount point.

---

### Post by Cheesemill on 2010-01-18
One thing Grenage forgot:

You have to manually create the mount point first:
```
sudo mkdir /mnt/archive
```
It doesn't have to be archive, you can call it whatever you want.

---

### Post by Grenage on 2010-01-18
Good call; I also forgot to add that you can test the new fstab by using:

```
sudo mount -a
```

You can check for errors without rebooting.

---

### Post by chuina on 2010-01-18
Also, get the exact /dev/... by

```
sudo fdisk -l
```

---

### Post by ankspo71 on 2010-01-18
Hi,
I always had trouble with this, so I use a program called pysdm.
After installing it has a shortcut called Storage Device Manager.
The only options I fiddled with is...
"Allow any user to mount the file system"
"The file system is mounted at boot time"

It made an entry for me like this in fstab:
/dev/sdb1   /media/sdb1    ext4   users     0  0 
I assume it made the mount point for me because it used to have a long uuid type mount point.

Now I'm not prompted for a password and it is automatically mounted at boot.

Anyways, it works for me, so if you have trouble getting a drive to mount automatically, then give pysdm a try.

---

### Post by Grenage on 2010-01-18
> used to have a long uuid type mount point

UUID are preferable (apparently), but that will work just as well 99% of the time.

---

### Post by Paqman on 2010-01-18
> **ankspo71 said:**
> give pysdm a try.

For an Absolute Beginner, this is the way to go. It's an excellent tool.

---

### Post by Sejanus on 2010-01-18
Thanks guys, everything works! sudo mount -a was especially usefull 'cause I did need to re-edit /etc/fstab several times till I got it right (mainly because at first I was trying to mount it to already existing mount dir, e.g. one to which I mounted it manually). Appreciate your help ;)

---

