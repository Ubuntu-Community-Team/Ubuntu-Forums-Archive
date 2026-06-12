---
title: "strange ubuntu problem"
date: 2009-09-29
forum: New to Ubuntu
---

### Post by amarumayo on 2009-09-29
Very strange problem.  Got home from work.  Booted up ubuntu. Gnome is a bit different, my places folder menu no long has documents, photos, videos, etc.  Mozilla not working.  But the strangest thing is it is assuming my hard drive is full.  If I make a text file with one word I can';t even save that without an insufficient disk space error. I ran properties on my disc and it only lists 83GB of stuff (250GB) hard drive but it says available space 0 at the bottom.  What the heck has happened?

---

### Post by nhasian on 2009-09-29
can you give us the output of the following terminal commands:

```
sudo fdisk -l
```
```
df -h
```
```
free -m
```


> **amarumayo said:**
> Very strange problem.  Got home from work.  Booted up ubuntu. Gnome is a bit different, my places folder menu no long has documents, photos, videos, etc.  Mozilla not working.  But the strangest thing is it is assuming my hard drive is full.  If I make a text file with one word I can';t even save that without an insufficient disk space error. I ran properties on my disc and it only lists 83GB of stuff (250GB) hard drive but it says available space 0 at the bottom.  What the heck has happened?

---

### Post by amarumayo on 2009-09-29
Ok here are the outputs:

bird@bird-laptop:~$ sudo fdisk -l
[sudo] password for bird: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004bcfe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29298   235336153+  83  Linux
/dev/sda2           29299       30401     8859847+   5  Extended
/dev/sda5           29299       30401     8859816   82  Linux swap / Solaris
bird@bird-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             221G  221G     0 100% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  104K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  148K  1.5G   1% /dev
tmpfs                 1.5G  184K  1.5G   1% /dev/shm
lrm                   1.5G  2.2M  1.5G   1% /lib/modules/2.6.28-15-generic/volatile
overflow              1.0M   16K 1008K   2% /tmp
bird@bird-laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2955       1309       1646          0        138        648
-/+ buffers/cache:        522       2433
Swap:         8652          0       8652
bird@bird-laptop:~$

---

### Post by drs305 on 2009-09-29
Yep, your partition is full. My best guess is you had a backup that saved to your / instead of to a backup partition that wasn't mounted at the time of the backup.

Here is a disk space troubleshooting guide that may help you find out what happened:
[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

If you need to immediately gain some space, try running:
```
sudo apt-get clean
```
to clear your package cache.

---

### Post by amarumayo on 2009-09-29
Ok that was it.  Thanks.  I pointed Sbackup in the wrong place and forgot I even had set that up.

---

