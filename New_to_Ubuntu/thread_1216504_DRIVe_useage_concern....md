---
title: "DRIVe useage concern..."
date: 2009-07-18
forum: New to Ubuntu
---

### Post by NOTAGEEK on 2009-07-18
can someone explain /dev/sr0 below ???  should the 100%use be a concern ???  what does it mean ???

thanks...



 df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              19G  2.6G   15G  15% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  100K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  144K  1.5G   1% /dev
tmpfs                 1.5G     0  1.5G   0% /dev/shm
lrm                   1.5G  2.2M  1.5G   1% /lib/modules/2.6.28-13-generic/volatile
/dev/sda2             184G  332M  174G   1% /home
/dev/sr0              388K  388K     0 100% /media/cdrom0

---

### Post by sisco311 on 2009-07-18
sr0 is the first optical disc drive in your system.

df always reports optical discs as 100% full.

---

### Post by NOTAGEEK on 2009-07-18
> **sisco311 said:**
> sr0 is the first optical disc drive in your system.

df always reports optical discs as 100% full.


i kinda thought that but wanted to be sure... thanks...

thread solved...

---

