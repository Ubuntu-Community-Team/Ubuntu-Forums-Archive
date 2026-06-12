---
title: "mounting issues"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by jmd9qs on 2009-01-15
hi all,

i recently created an ext3 partition on my internal drive to dual-boot mandriva 1. i wanted to transfer some files from my ubuntu partition to the mandriva one, so i tried to mount the mandriva partition with sudo. here is what i get back:

```
jmd9qs@jmd9qs-desktop:/media$ sudo mount Mandriva/
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

the weird part is if i use gparted, i can mount /media/Mandriva no problem... any idea why this is and how i can fix it? it's not a real issue, seeing as i am able to mount it w/ gparted, i'd just like to know in case it happens agan (and for general knowledge!)

thanks

jmd9qs

---

### Post by Vantrax on 2009-01-16
You could add it to fstab as a long term solution, but id try getting it working via a manual mount first.

Find out what disk it is on the drive by running sudo fdisk -l

your looking for a value of sda1 sda2 or if its on its own disk maybe sdb1 or sdb2l. You should be able to work it out (ill assume its sda2).

make a directory to mount, then mount:
sudo mkdir /media/mandrivia
sudo mount /dev/sda2 /media/mandrivia

should work fine that way.

---

### Post by jmd9qs on 2009-01-19
thanks that worked fine.

---

