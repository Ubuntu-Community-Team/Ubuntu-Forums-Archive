---
title: "hard drive capacity off"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by ash2525 on 2009-02-20
Hi i have a 80gb ide hard drive with one partition and in disk usage analyzer it says it has a capacity of 142.1gb.

I am using ubuntu 8.04. [-(

---

### Post by LowSky on 2009-02-20
That seems odd, around here we ask for proof...

please go to terminal and type, 
```
df -H
```

then paste results

Thanks

---

### Post by mcduck on 2009-02-20
In Disk Usage Analyzer, go to Edit/Preferences and disable "gvs-fuse-daemon". Having that enabled causes the disk capacity to report as doubled. (it's a virtual file system used by Gnome, and shouldn't even be enabled in Disk Usage Analyzer by default as it makes no sense when thinking about real disk space)

---

### Post by ash2525 on 2009-02-20
heres what you needed.



a@ubuntu:~$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda1               77G   5.6G    67G   8% /
varrun                 530M   103k   530M   1% /var/run
varlock                530M      0   530M   0% /var/lock
udev                   530M    54k   530M   1% /dev
devshm                 530M    13k   530M   1% /dev/shm
lrm                    530M    41M   489M   8% /lib/modules/2.6.24-23-generic/volatile
gvfs-fuse-daemon        77G   5.6G    67G   8% /home/a/.gvfs
a@ubuntu:~$ 


Here is a picture or it "http://g.imagehost.org/0215/Screenshot-Disk_Usage_Analyzer.png"

Should i just ignore this?

---

### Post by ash2525 on 2009-02-20
Never mind i did what mcduck sayed and it worked. Thanks to any one who looked at this thread.:mrgreen::mrgreen::mrgreen::mrgreen::mrgreen::mrgreen:

---

