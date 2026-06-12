---
title: "confuesd with mounting"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by unitedoceanic on 2009-11-18
Hi there newbie here ):P ,

i'm still learning my way through ubuntu and have to say many things are still confusing.

i have 4 partitions 

sda1 XP
sda2 ubuntu
sda3 swap
sda4 music/videos/pictures

i had a few problems setting up the partitions and had to reinstall xp & ubuntu twice. however everything runs smooth now but i made a small error.

sda1 is mounted as /windows and sda4 is mounted as /dos
 
i would like to see the partitions, the way i see my external drive

thanks for any advice you can give me

---

### Post by sisco311 on 2009-11-18
Mount them in the /media directory.

[list]
[*]  unmount the partitions:
```
sudo umount /windows
sudo umount /dos
```

[*]  Edit the /etc/fstab file:
```
gksu gedit /etc/fstab
```

In the file the second column is the mount point.

[*]  Replace /windows (/dos) with /media/windows (/media/dos).

[*]  Create the new mount points:
```
sudo mkdir /media/windows
sudo mkdir /media/dos
```

[*]  Mount the partitions:
```
sudo mount -a
```
[/list]

---

### Post by nothingspecial on 2009-11-18
```
sudo mkdir /name/of/partition
```

```
sudo mount /dev/sda? /name/of/partition
```

To make this permanent you are going to have to edit /etc/fstab

First find the UUID of each partition

```
sudo blkid
```

Then add an entry to /etc/fstab. For example here are my 2 music drives in fstab

```
UUID=b80dc834-e5ed-423c-8538-0fb448d0d34c /media/music    ext3    relatime,noexec  0       2
UUID=48e6d536-a3dc-4d59-88a0-1d291cb1bb27 /media/backup   ext3    relatime,noexec  0       2
```

---

### Post by unitedoceanic on 2009-11-18
fantastic, thank you both!

---

