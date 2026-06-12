---
title: "[SOLVED] Can't believe I'm asking this..."
date: 2008-12-30
forum: New to Ubuntu
---

### Post by caro on 2008-12-30
I bought my computer two years ago with Ubuntu already loaded (Dell) so I've never done an install.  My dumb question is:  how can I tell if I have a home partition versus a home folder?  :confused:

I've considered doing a fresh install next time (no good reason) but certainly don't want to lose all my files and data.  

Thanks in advance!

---

### Post by taurus on 2008-12-30
I think some people call it the home folder (coming from windows) but it should be called /home partition.  I guess you want to know whether you have a separate /home partition.

Applications -> Accessories -> Terminal
```
df -h
```
If you don't see /home on the list, then you don't have a separate /home partition.

---

### Post by poebae on 2008-12-30
If you use Gparted or a different partition editor, you'll see what your disk partitioning looks like.

If you have a separate home partition, you'll see a separate partition mounted as /home.

I haven't used a pre-loaded Dell computer, but my best guess is that a pre-installed version of Ubuntu would simply have a home folder rather than a home partition.

---

### Post by tuxxy on 2008-12-30
Dell dont make them with /home partitions so you could either shrink your current partition with gparted using the Live CD then create a new /home partition and add the mount point as /home

---

### Post by caro on 2008-12-30
That's what I was afraid of....

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              71G  4.0G   64G   6% /
tmpfs                 247M     0  247M   0% /lib/init/rw
varrun                247M  100K  247M   1% /var/run
varlock               247M     0  247M   0% /var/lock
udev                  247M  2.7M  244M   2% /dev
tmpfs                 247M   24K  247M   1% /dev/shm
/dev/sda3             193M   16M  168M   9% /boot
tmpfs                 247M  2.0M  245M   1% /lib/modules/2.6.27-9-generic/volatile
caro@dell:~$ 


Thanks for the quick response!

---

### Post by theozzlives on 2008-12-30
or check the free space of / compared to /home if they don't match, you have a seperate /home

---

### Post by tuxxy on 2008-12-30
No problem and heres a good guide for creating the seperate /home partition

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by caro on 2008-12-30
> **tuxxy said:**
> No problem and heres a good guide for creating the seperate /home partition

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

I hoped I wouldn't have to do that...sounds like a project for a day when I have some time to kill.

---

### Post by tuxxy on 2008-12-30
Yes it will kill some time :p depending on your HD size it could be a lot of time, took me around 4 hours once to shrink a 300GB+ partition :(

---

