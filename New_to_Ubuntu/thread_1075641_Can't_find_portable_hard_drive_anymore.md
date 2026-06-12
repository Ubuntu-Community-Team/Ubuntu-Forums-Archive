---
title: "Can't find portable hard drive anymore"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by larry412 on 2009-02-20
My system will no longer recognize my portable hard drive.  I do not know why this happened but I think the drive was unmounted improperly while I was at work.  I have been checking forums for answers and nothing works.  I have had this problem for about two weeks.  I cannot find the drive in my system anywhere.  Any ideas would be appreciated.

---

### Post by taurus on 2009-02-20
Plug it in.  Then, open a terminal and post the outputs of these commands.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
df -h
```

---

### Post by larry412 on 2009-02-20
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6ba5261e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9542    76646083+  83  Linux
/dev/sda2            9543        9726     1477980    5  Extended
/dev/sda5            9543        9726     1477948+  82  Linux swap / Solaris
cats@freekbox:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              73G  8.5G   61G  13% /
varrun                1.5G  212K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G   48K  1.5G   1% /dev
devshm                1.5G   12K  1.5G   1% /dev/shm
lrm                   1.5G   39M  1.5G   3% /lib/modules/2.6.24-23-generic/volatile
gvfs-fuse-daemon       73G  8.5G   61G  13% /home/cats/.gvfs

This is my internal hard drive.  I have a Seagate Free Agent 500 gig external hard drive that worked without any problem until a couple of weeks ago. I came home from work and the computer was off but the hard drive was not.  Now it is on from the time I boot my computer until I unplug the portable hd.

---

### Post by LowSky on 2009-02-20
connect it to a MS Windows machine, let it load up then disconnect it correctly. then try it on the Linux machine.

NTFS formatted drives can sometimes be a pain in the rear end.

---

### Post by larry412 on 2009-02-21
I don't have a windows machine and the only access to one is at work and I don't think they would approve of that.

---

