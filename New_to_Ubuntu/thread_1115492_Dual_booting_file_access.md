---
title: "Dual booting file access"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by m3bik on 2009-04-03
I have Windows XP and Ubuntu Server 8.10 installed on a spare computer. While in Ubuntu, is there a way to access the files from the Windows side of the hard drive?

---

### Post by asmoore82 on 2009-04-03
GUI or command line?

---

### Post by m3bik on 2009-04-03
Command line...

---

### Post by asmoore82 on 2009-04-04
you will need to know the device of your win partition - let's use "/dev/sda1" as an example
the output of this can help you find it:
```
sudo fdisk -l
```
^^ it will do a read only listing of partitions

you will need a folder to use as the mount point of the win partition - let's use "/media/windoze" as an example

you can mount it from the command line:
```
sudo mount -t ntfs-3g /dev/sda1 /media/windoze
```
and unmount it when you are done with it:
```
sudo umount /media/windoze
```

for a permanent solution, you could edit "/etc/fstab" and add a line something like this:
```
/dev/sda1   /media/windoze   ntfs-3g   defaults,user,noauto   0   0
```
"noauto" means it won't be mounted at every boot
"user" means that non-root users are allowed to mount/unmount it

once it is a valid entry in fstab, you can mount/unmount it by only specifying the mount-point:
```
mount /media/windoze
umount /media/windoze
```

---

