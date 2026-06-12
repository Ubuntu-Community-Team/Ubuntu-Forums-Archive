---
title: "wont mount my sanyo dlx 8500"
date: 2009-07-05
forum: New to Ubuntu
---

### Post by amchornet on 2009-07-05
I just want to manage my pics and music. Ubuntu trys to mount it but cant it says unable to mount  mount:special device/dev/sdb1 does not exist.  If I install a usb stick it had no problem with that just the phone. Any help would be awesome.

---

### Post by Dark006 on 2009-07-05
It gives an error when you plug it in? You could try this and see if it works.
```
sudo mkdir /mount/sanyo
sudo mount /dev/sdb1 /mount/sanyo

```

---

### Post by amchornet on 2009-07-06
ok I tried that and got 
dad@dad-laptop:~$ sudo mkdir /mount/sanyo
[sudo] password for dad: 
mkdir: cannot create directory `/mount/sanyo': No such file or directory

I am not sure what to do from here when i fdisk i get--

 Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
  .

---

