---
title: "none partition listed in df -kh ?"
date: 2010-10-27
forum: New to Ubuntu
---

### Post by albertwt on 2010-10-27
Hi All,

Why there are some unknown partition in my Linux installation ?

```

root@SSV:~# **df -kh**

Filesystem            Size Used Avail Use% Mounted on
/dev/mapper/SSV-root   19G  1.2G   17G   7% /
[B]none                  243M  176K  242M   1% /dev
none                  247M     0  247M   0% /dev/shm
none                  247M   40K  247M   1% /var/run
none                  247M     0  247M   0% /var/lock
none                  247M     0  247M   0% /lib/init/rw
none                   19G  1.2G   17G   7% [/B]/var/lib/ureadahead/debugfs
/dev/sda1             228M   17M  199M   8% /boot

root@SSV:~# uname -a
Linux SSV 2.6.32-24-server #39-Ubuntu SMP Wed Jul 28 06:21:40 UTC 2010 x86_64 GNU/Linux


```

This is just a clean install of the server with LVM, can anyone explain here please ?

Thanks

---

### Post by anarchy404 on 2010-10-27
My BIOS is wonky and attempts to make a software raid so I get partitions named /dev/nvidiaXXX/ (where each X is a number) that I can't write to alongside of my normal partitions /dev/sda, etc. Perhaps that's the issue that you have going on here. Just try to delete them and move on.

---

### Post by albertwt on 2010-10-27
thanks man,

which one to delete ? using FDISK ?

---

### Post by worldwithoutgurus on 2010-10-27
NO! Your system need them to function properly! Leave them alone!

[http://ubuntuforums.org/showthread.php?t=1400580](http://ubuntuforums.org/showthread.php?t=1400580)
[http://www.cyberciti.biz/tips/what-is-devshm-and-its-practical-usage.html](http://www.cyberciti.biz/tips/what-is-devshm-and-its-practical-usage.html)
[http://www.pathname.com/fhs/](http://www.pathname.com/fhs/)

---

### Post by anarchy404 on 2010-10-27
It's really just easier to use gparted for some stuff. Plus you have a smaller chance of messing up because of typos and what not. You should also change your bios settings or at least check them to make sure that it's a software raid issue as it might not be.

Best of luck.

---

### Post by anarchy404 on 2010-10-28
Oh my goodness. Yeah, listen to worldwithoutgurus. Don't do what I just suggested :(

---

### Post by albertwt on 2010-10-29
ah.. ok, so I'll leave it alone then.

I appreciate your suggestion and explanation @worldwithoutgurus

Thanks mate.

---

