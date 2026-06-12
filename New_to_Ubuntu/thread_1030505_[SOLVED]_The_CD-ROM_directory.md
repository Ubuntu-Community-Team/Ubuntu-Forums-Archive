---
title: "[SOLVED] The CD-ROM directory"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by eckeroo on 2009-01-04
I need to know the precise name of my CD Drive [hdc/hdd etc], I've been told that dev/cdrom is just a link to it. What programs can I run to find out the precise name of all my CD and DVD drives?

Thanks

Hardy Heron 8.04

*additional*

How can I get the title of My threads in bold text?

---

### Post by northern lights on 2009-01-04
Run```
sudo lshw -C disk
```

---

### Post by Captaingracekidd on 2009-01-31
Recentlu installed Intrepid from live disc and did all the updates. The cd-rom doesnt exist. Help.

```
 sudo lshw -class disk
  *-disk                  
       description: ATA Disk
       product: TOSHIBA MK3252GS
       vendor: Toshiba
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: LV01
       serial: 585FF2RLS
       size: 298GiB (320GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=5eb0aa6b

```

Shows no cd rom.

```
ls -al /media
total 12
drwxr-xr-x  3 root root 4096 2008-10-29 20:53 .
drwxr-xr-x 22 root root 4096 2009-01-31 12:51 ..
lrwxrwxrwx  1 root root    6 2009-01-30 18:07 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2009-01-30 18:07 cdrom0

```

/etc/fstab states:

```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

It seems my machine has no idea I even have a cd rom. When inserting cds and dvds the cd rom spins them but nothing else happens.

---

