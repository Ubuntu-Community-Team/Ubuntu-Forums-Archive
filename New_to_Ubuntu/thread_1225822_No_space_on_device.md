---
title: "No space on device"
date: 2009-07-29
forum: New to Ubuntu
---

### Post by kpsg25690 on 2009-07-29
[FONT=Comic Sans MS][SIZE=4][SIZE=3]I installed ubuntu 9.04 a few days back and it's going fine.
but i have some problems.
When downloading something to the desktop i got a message no space on device left.
i installed ubuntu inside windows but on a separate partition that is 16GB(ntfs).I googled it and got some results but cannot understand the commands as i am new to ubuntu and linux.
thanks for the help in advance[/SIZE]. :P
[/SIZE][/FONT]

---

### Post by llamabr on 2009-07-29
Hi.  That's fine.  in a terminal, do this:

```
sudo apt-get clean
```

and then post the output of 

```
df -h
```

---

### Post by kpsg25690 on 2009-07-29
Here's the output:-


Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                      4.6G  3.7G  648M  86% /
tmpfs                 755M     0  755M   0% /lib/init/rw
varrun                755M  112K  754M   1% /var/run
varlock               755M     0  755M   0% /var/lock
udev                  755M  172K  754M   1% /dev
tmpfs                 755M  184K  754M   1% /dev/shm
/dev/sdb6              17G  5.7G   11G  36% /host
lrm                   755M  2.2M  752M   1% /lib/modules/2.6.28-13-generic/volatile
/dev/sda6              31G   23G  8.5G  73% /media/software
/dev/sdb5              39G   30G  9.1G  77% /media/Games
/dev/sda1              20G   16G  4.5G  78% /media/movies
/dev/sda5              25G   18G  7.3G  71% /media/Karan

---

### Post by MelDJ on 2009-07-29
try this thread: [http://ubuntuforums.org/showthread.php?t=1224949&highlight=hard+disk](http://ubuntuforums.org/showthread.php?t=1224949&highlight=hard+disk)
:KS

---

### Post by kpsg25690 on 2009-07-30
thanks for help but i reinstalled ubuntu with a 15 gb installation i previously choose 5 gb installation.
that created a 5 gb virtual disk which seemed to be the problem.

---

