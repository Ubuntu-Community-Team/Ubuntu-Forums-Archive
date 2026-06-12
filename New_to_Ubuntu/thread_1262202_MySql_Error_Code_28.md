---
title: "MySql Error Code 28"
date: 2009-09-09
forum: New to Ubuntu
---

### Post by Mission 10 on 2009-09-09
I keep getting this error code when I try to do a mysqldump. 
```
OS error code  28:  No space left on device
```

I prevously had sbackup installed but it had issues and kept replicating backups and filled up my hard drive 100%. I solved that issue but I still get this error code. I've posted the results of df -h below. I think that since the drive was full it may have corrupted the tables but I'm not sure. Any ideas?

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              71G   12G   56G  18% /
varrun                759M  120K  759M   1% /var/run
varlock               759M     0  759M   0% /var/lock
udev                  759M   52K  759M   1% /dev
devshm                759M   48K  759M   1% /dev/shm
lrm                   759M   40M  720M   6% /lib/modules/2.6.24-24-generic/volatile
overflow              1.0M  1.0M     0 100% /tmp
/dev/sdb1             1.9G  635M  1.3G  34% /media/USB DISK


```

---

### Post by Mission 10 on 2009-09-09
Interestingly enough I get a new cryptic error when I try and sudo nautilus...

```

(nautilus:15438): Eel-WARNING **: GConf error:
  Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: IOR file '/tmp/gconfd-root/lock/ior' not opened successfully, no gconfd located: No such file or directory 2: IOR file '/tmp/gconfd-root/lock/ior' not opened successfully, no gconfd located: No such file or directory)

```

---

