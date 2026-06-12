---
title: "Data lost in a catastrophic error."
date: 2009-12-27
forum: New to Ubuntu
---

### Post by peace.gangsta on 2009-12-27
I installed ubuntu 8.04 using a .iso from a cd.I used umenu.exe bad part > i chose C drive(from the 3 drives in all C,D,E,,C being primary and had windows)when it asked for some 10 Gb space .
Now I have surprisingly lost all my data in drives D and E.
And the total space has now reduced to 270 G ... I have a hard drive of 320 gb.
Now this is suffocating me up!
Please help if I can recover some of the lost files if not all of them.I used Recuva in windows to recover permanently deleted&non-overwritten files,is there any similar tool in Ubuntu/
And please explain why the hell has my disk space reduced to 270 gb.
Also if I can recover the rest of the space , if its hidden somewhere.
Initial Partitions were C&D drive - 50 Gb each and E of 200 Gb.

---

### Post by taurus on 2009-12-27
I wasn't there so I would not know whether you told the installer to use that partition or use the _whole harddrive_.  However, open a terminal and post the outputs of these commands to be sure if you have wiped out everything on it when you installed Ubuntu.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
df -h
```
And if you are trying to recovery some windows files on it, better stop using the machine because the more you write to disk, the harder it is to recover.  See if this app can help you with the recovery process.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by peace.gangsta on 2009-12-27
The output to the code sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2f61b97a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37780   303467818+  83  Linux
/dev/sda2           37781       38913     9100822+   5  Extended
/dev/sda5           37781       38913     9100791   82  Linux swap / Solaris




and that to df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             288G  3.3G  270G   2% /
varrun                1.5G  124K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G   44K  1.5G   1% /dev
devshm                1.5G  116K  1.5G   1% /dev/shm
lrm                   1.5G   38M  1.5G   3% /lib/modules/2.6.24-16-generic/volatile
gvfs-fuse-daemon      288G  3.3G  270G   2% /home/abhinav/.gvfs

---

### Post by taurus on 2009-12-27
Looks like you told the installer to use the whole harddrive.  ](*,)

---

### Post by Cheesemill on 2009-12-27
Just restore all your data from your most recent backup.

---

### Post by peace.gangsta on 2009-12-28
okay well i restored many files which were not overwritten ..
Thanks a lot !
Can anyone please explain why is the file system properties showing only 270 Gb as the total?
And how can i recover the rest of the space.

---

