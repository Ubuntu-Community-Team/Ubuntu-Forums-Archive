---
title: "New Partition......"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by endlessurf on 2008-12-24
I have a windoz partition and then my Linux partitions.  My only issue is I have a ntfs partition that I would Like to mount ever time I use Linux.  I searched for awhile and came up empty handed.  any help would be nice.

---

### Post by reydempto on 2008-12-24
If what you're saying is that your windows partition mounts fine, you just want to make it mount at startup, then this should work.

Just add the following to the /etc/fstab file
Code:

sudo vi /etc/fstab

substitute 'vi' for whatever editor you want, just remember you need to do sudo in order to edit the file
and add the line
Code:

/dev/hda2       /mnt/windows    ntfs    umask=0222      0       0

Just make sure that the folder (in this case /mnt/windows/) exists and where it says ntfs change it to vfat IF the partition is fat32 or leave it as it is for ntfs

---

### Post by Elfy on 2008-12-24
Install ntfs-config from a terminal do

```
sudo apt-get install ntfs-config
```

When it's done the tool is in System Tools - logical from there, it will get added to fstab. Reboot and it should be there for you.

---

### Post by reydempto on 2008-12-24
> **forestpixie said:**
> Install ntfs-config from a terminal do

```
sudo apt-get install ntfs-config
```

When it's done the tool is in System Tools - logical from there, it will get added to fstab. Reboot and it should be there for you.

same difference :P

---

### Post by endlessurf on 2008-12-24
ok i'm right there, like most things I need help finishing, ie cars, homework, women, computers....... it gives me a devices as dev/sda5...... then it ask for a mount point..... i do not know what to put in here....help...

---

### Post by reydempto on 2008-12-24
for the mount point, use

/media/windows

that's what i did, anyways.

Lemme know how it goes, k?

---

### Post by Xiong Chiamiov on 2008-12-24
I don't know if the automagic GUI config does it for you or not, but when setting this up manually, you need to create the directory first:
```

sudo mkdir /media/windows

```

---

### Post by Elfy on 2008-12-24
> **reydempto said:**
> same difference :P
except when I posted you're post was to a link that dealt with something else :)

[http://ubuntuforums.org/showthread.php?t=1016578](http://ubuntuforums.org/showthread.php?t=1016578)

---

### Post by reydempto on 2008-12-24
> **forestpixie said:**
> except when I posted you're post was to a link that dealt with something else :)

Ah, i see.

good old 'edit'

---

### Post by Elfy on 2008-12-24
heh - I wouldn't have bothered otherwise :lol:

I prefer to do it manually myself as well

---

### Post by reydempto on 2008-12-24
> **forestpixie said:**
> heh - I wouldn't have bothered otherwise :lol:

I prefer to do it manually myself as well

totally, that way you can go to a different distro and still pretty much know what you're doing :)

---

### Post by logos34 on 2008-12-24
> **Xiong Chiamiov said:**
> I don't know if the automagic GUI config does it for you or not, but when setting this up manually, you need to create the directory first:
```

sudo mkdir /media/windows

```

yeah, I can't seem to remember, either.  I thought it created the mp for you if it doesn't exist already...wish someone would confirm that (been a long time since I had windows partitions on my machine)

---

### Post by Elfy on 2008-12-24
> **logos34 said:**
> yeah, I can't seem to remember, either.  I thought it created the mp for you if it doesn't exist already...wish someone would confirm that (been a long time since I had windows partitions on my machine)

Another one working from memory then :lol:

I'll be dual booting a friends soon I'll let you know :)

---

### Post by Elfy on 2008-12-24
> **logos34 said:**
> yeah, I can't seem to remember, either.  I thought it created the mp for you if it doesn't exist already...wish someone would confirm that (been a long time since I had windows partitions on my machine)

It does do so - name the mountpoint and it gets added to fstab and directory created.


Happy Xmas

---

### Post by logos34 on 2008-12-24
> **forestpixie said:**
> It does do so - name the mountpoint and it gets added to fstab and directory created.


Happy Xmas

thanx for nailing that down.  seasons greetings to you too!

---

