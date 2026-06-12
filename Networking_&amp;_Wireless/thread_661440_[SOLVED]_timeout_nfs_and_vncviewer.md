---
title: "[SOLVED] timeout nfs and vncviewer"
date: 2008-01-07
forum: Networking &amp; Wireless
---

### Post by stevieb on 2008-01-07
hello,

after updating from feisty to gutsy, nfs and vncviewer always timeout without connecting to my dapper server.

i've searched around for an answer, but have found nothing that works.  

here's the end of /etc/ssh/ssh_config:
```
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication no
    GSSAPIDelegateCredentials no

```

here's /etc/fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=7f0cb83b-3077-4bf0-ae17-bb6dff268639 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=3F6F-3E33  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=3a0e80e8-1c3b-4d29-b3c6-afc992a5447e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
192.168.1.6:/home/steve /home/steve/Desktop/cannonball  nfs     rsize=8192,wsize=8192,timeo=14,intr00

```

what other info can i post?  i haven't changed anything on the dapper server since upgrading the laptop from feisty to gutsy..

thanks,

steve

---

### Post by stevieb on 2008-01-08
the problem was my wireless card.  i could get onto the internet and surf just fine, but the use of a restricted driver somehow prevented xubuntu gutsy from seeing it and allowing configuration.

switching wireless cards did the trick for me. thanks to those who looked!

---

