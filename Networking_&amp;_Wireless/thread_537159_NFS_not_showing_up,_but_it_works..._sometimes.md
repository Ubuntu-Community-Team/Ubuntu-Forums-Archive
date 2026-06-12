---
title: "NFS not showing up, but it works... sometimes"
date: 2007-08-28
forum: Networking &amp; Wireless
---

### Post by motionsiren on 2007-08-28
I can confirm that the mounts ARE mounted but they are NOT showing up under mount. I am clearly confused.... Very discouraging.

```

toki:bkeating> cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

pendulum:/data/home             /data/home      nfs     rw,_netdev      0       0
pendulum:/data/vhosts           /data/vhosts    nfs     rw      0       0
pendulum:/data/svn-repos        /data/svn-repos nfs     rw      0       0
pendulum:/data/private          /data/private   nfs     rw      0       0

crunch:/Rosetta /mnt/crunch.longnow.org/rosetta nfs     ro      0       0
crunch:/Design  /mnt/crunch.longnow.org/design  nfs     rw      0       0
crunch:/media   /mnt/crunch.longnow.org/media   nfs     ro      0       0



toki:bkeating> sudo mount -a
mount: pendulum:/data/home already mounted or /data/home busy
mount: pendulum:/data/vhosts already mounted or /data/vhosts busy
mount: pendulum:/data/svn-repos already mounted or /data/svn-repos busy
mount: pendulum:/data/private already mounted or /data/private busy
mount: crunch:/Rosetta already mounted or /mnt/crunch.longnow.org/rosetta busy
mount: crunch:/Design already mounted or /mnt/crunch.longnow.org/design busy
mount: crunch:/media already mounted or /mnt/crunch.longnow.org/media busy



toki:bkeating> df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             7.6G  753M  6.5G  11% /
varrun                 78M   68K   78M   1% /var/run
varlock                78M  4.0K   78M   1% /var/lock
udev                   78M   52K   78M   1% /dev
devshm                 78M     0   78M   0% /dev/shm

```

---

### Post by dcherryholmes on 2007-08-30
I just noticed the same thing with two Feisty workstations.  I have a Dapper server and this doesn't seem to be a problem.

---

### Post by motionsiren on 2007-08-31
really annoying... seems to work tho..

---

