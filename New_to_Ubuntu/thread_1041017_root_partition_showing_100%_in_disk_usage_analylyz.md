---
title: "/  root partition showing 100% in disk usage analylyzer"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by pretender? on 2009-01-16
When i scan all folders im disk analyzer z displays 100% useage 

How ever when i run df -h i get the below output 

Filesystem            Size Used Avail Use% Mounted on
/dev/sda6              12G  3.3G  7.3G  31% /
tmpfs                 505M     0  505M   0% /lib/init/rw
varrun                505M  224K  505M   1% /var/run
varlock               505M     0  505M   0% /var/lock
udev                  505M  2.8M  502M   1% /dev
tmpfs                 505M  564K  505M   1% /dev/shm
lrm                   505M  2.0M  503M   1% /lib/modules/2.6.27-9-generic/volatile
df: `/proc/bus/usb/.usbfs': No such file or directory
/dev/sda7              93G   13G   76G  15% /home


To me df indicates that only 31% usage which is correct

I think i am running out of room as mythtv no longer records 

I am running Ubuntu 8.10 and have a separate home partition

---

### Post by stevoo on 2009-01-16
you are definetely not running out of space.... 

/dev/sda6 12G 3.3G 7.3G 31% /
/dev/sda7 93G 13G 76G 15% /home

But it all depends where you MythTv Records

---

### Post by pretender? on 2009-01-16
mythtv recordings /va/lib/mythtv/recordings

disk analyzer screen dump attached

---

