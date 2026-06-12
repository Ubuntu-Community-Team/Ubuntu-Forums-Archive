---
title: "Full folders in file system"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by grouchyolddude on 2009-01-20
return from df-h command
> Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              25G   25G     0 100% /
varrun                506M  276K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   56K  506M   1% /dev
devshm                506M   60K  506M   1% /dev/shm
lrm                   506M   39M  467M   8% /lib/modules/2.6.24-23-generic/volatile
/dev/sda1              68G   25G   40G  39% /home
overflow              1.0M   40K  984K   4% /tmp
gvfs-fuse-daemon       25G   25G     0 100% /home/o/.gvfs

  I can see that 2 folders are full. I beleve it's creating an error 
Any advice on cleaning theses up?
Can I delete anything critical to my system from them?

 I have reason to think it may possibly be related to a backup I performed yesterday useing Simple Backup.Default to backup 
/var/
/home/
/user/local/
/ect/
 Did I backup to much?

---

### Post by hyper_ch on 2009-01-21
I thinkt here might be a lot in your trash...

---

### Post by theozzlives on 2009-01-21
> **hyper_ch said:**
> I thinkt here might be a lot in your trash...

If not, resize some of your partitions to make room for the full ones.

---

### Post by grouchyolddude on 2009-01-21
> **hyper_ch said:**
> I thinkt here might be a lot in your trash...
Hmm my trash says it's empty. 
I deleted an old backup file and freed up 15% of one, but I'm still getting an error when I try to dl an email attachment. 
Here's the return from command now
> Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda2     ext3     25G   20G  3.8G  85% /
varrun       tmpfs    506M  280K  506M   1% /var/run
varlock      tmpfs    506M     0  506M   0% /var/lock
udev         tmpfs    506M   56K  506M   1% /dev
devshm       tmpfs    506M  368K  506M   1% /dev/shm
lrm          tmpfs    506M   39M  467M   8% /lib/modules/2.6.24-23-generic/volatile
/dev/sda1     ext3     68G   25G   40G  39% /home
overflow     tmpfs    1.0M  1.0M     0 100% /tmp
gvfs-fuse-daemon
fuse.gvfs-fuse-daemon     25G   20G  3.8G  85% /home/o/.gvfs

  .


overflow     "tmpfs    1.0M  1.0M     0 100% /tmp"
I'm pretty new, but something about that line doesn't seem right to me??
 other than saying it is 100% full..
How much space is 1.OM ??
"overflow"?? should that be telling me something?
 and I fail to find anything named overflow in the file system.
Am I way off base here?

---

### Post by grouchyolddude on 2009-01-21
Solved..
 > sudo  rm -rf /tmp/*

> filesystem    type    size  used avail use% mounted on
/dev/sda2     ext3     25g   20g  3.8g  85% /
varrun       tmpfs    506m  280k  506m   1% /var/run
varlock      tmpfs    506m     0  506m   0% /var/lock
udev         tmpfs    506m   56k  506m   1% /dev
devshm       tmpfs    506m  368k  506m   1% /dev/shm
lrm          tmpfs    506m   39m  467m   8% /lib/modules/2.6.24-23-generic/volatile
/dev/sda1     ext3     68g   25g   40g  39% /home
overflow     tmpfs    1.0m   28k  996k   3% /tmp
gvfs-fuse-daemon
fuse.gvfs-fuse-daemon     25g   20g  3.8g  85% /home/o/.gvfs


---

