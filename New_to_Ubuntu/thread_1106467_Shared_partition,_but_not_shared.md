---
title: "Shared partition, but not shared?"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by solissydney on 2009-03-25
Hi there.
I am dual booting Ubuntu with Win XP.
I have a "shared" partition 
dev/sda5  fat 32   /dos
I am unable to make use of it using Ubuntu, it cant see it.
Should I mount it on something else, for example sda2 ??
I was thinking of using that partition for example for back-ups.
When I set up the initial partitions I understood that 'shared' meant shared by XP and Ubuntu.

Ken

---

### Post by taurus on 2009-03-25
Is it /dev/sda2 or /dev/sda5?

Open a terminal and post the outputs of these commands here to see exactly which partition is that fat32/vfat.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by solissydney on 2009-03-25
As above.
The partition is sda5

---

### Post by taurus on 2009-03-25
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sda5   /media/sda5   vfat  iocharset=utf8,umask=000  0  0
```
Save it and exit gedit editing window.  Now, create the new mount point and mount it.

```
sudo mkdir /media/sda5
sudo mount -a
df -h
```

---

