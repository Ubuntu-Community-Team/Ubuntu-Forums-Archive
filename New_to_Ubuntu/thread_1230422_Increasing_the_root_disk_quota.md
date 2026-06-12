---
title: "Increasing the root disk quota"
date: 2009-08-03
forum: New to Ubuntu
---

### Post by randomlinux on 2009-08-03
Hi Guys,
I have installed my first ever linux on a laptop via the windows installer.
I have hit the 30G limit that I entered when I set up Ubuntu. My disk
partition is 40G. 
 
I am trying to use resize_reiserfs to add another 10G, but I cant seem to
specify the correct drive root.
 
Im not even sure if this is what I should be using.
 
cheers
rl

---

### Post by randomlinux on 2009-08-03
[FONT=Courier New]Here is a breakdown of my system

Dude>sudo fdisk -lu
[sudo] password for administrator: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xed1f86f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   213963119   106981528+   7  HPFS/NTFS
/dev/sda2       213963120   228024719     7030800   12  Compaq diagnostics
/dev/sda3       228024720   312575759    42275520    7  HPFS/NTFS
Dude>df
Filesystem           1K-blocks      Used Available Use% Mounted on
/host/ubuntu/disks/root.disk
                      28097104  25638336   1042756  97% /
varrun                  504824       108    504716   1% /var/run
varlock                 504824         4    504820   1% /var/lock
udev                    504824        60    504764   1% /dev
devshm                  504824        12    504812   1% /dev/shm
lrm                     504824     39792    465032   8% /lib/modules/2.6.24-23-generic/volatile
gvfs-fuse-daemon      28097104  25638336   1042756  97% /home/administrator/.gvfs

[/FONT]

---

### Post by jonathanysp on 2009-08-03
do you mean the windows installer as in wubi? if you used wubi to install im not sure how to partition it...but if you installed it on an actual partition, you can boot up with the gparted livecd, this will make modifying all the paritions much easier

---

### Post by LewRockwell on 2009-08-03
it's ok to try out other distros via their LiveCD function

it's ok to try out other distros via some sort of virtual sandbox

it's ok to try out other distros via some sort of windows shenanigans

but in the end you will be much better off and better served by having individual operating systems on their own partitions

thank you for your thread

[http://ubuntuforums.org/showthread.php?p=6296342](http://ubuntuforums.org/showthread.php?p=6296342)

.

---

### Post by randomlinux on 2009-08-03
Ive tried gparted, but I dont think thats really my issue. My quota is set to 30G. There is another 10G avaiable on the same partition that I want to expand ubuntu into. Its not used by windows.
I think I probally did use the wubi, I just followed the instructions on the www site.

---

### Post by randomlinux on 2009-08-03
I think I have misunderstood something here, does the way that I have installed ubuntu affect the performance? Should I reinstall? At the time I just though that it was easier to install it through windows.  Im guessing this was an error?

---

### Post by ajgreeny on 2009-08-03
> **randomlinux said:**
> I think I have misunderstood something here, does the way that I have installed ubuntu affect the performance? Should I reinstall? At the time I just though that it was easier to install it through windows.  Im guessing this was an error?
No, it wasn't an error, it's just another way of using and trying ubuntu without the need for partitioning.  If you then decide you don't want to use it you can simply uninstall it from windows in the same way you would any other application, with Control Panel, Add/Remove Applications, or whatever vista calls it these days.

Some people say that the system is slower when run through windows with wubi, but I have no experience of wubi use so can't comment on that, but I do agree that for the full effect of your ubuntu experience you should find it better if you use a normal dual boot system, partitioning and installing ubuntu on its own partitions.

It is very easy to do, so have a look through this site for all the info you might need.
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

---

### Post by randomlinux on 2009-08-03
cool, so if I install it properly ill get access to my full partition.

---

### Post by sydbat on 2009-08-03
> **randomlinux said:**
> cool, so if I install it properly ill get access to my full partition.Yup.

---

### Post by randomlinux on 2009-08-05
I would just like to say thanks for the help in understanding this issue. Installed ubuntu in a bit of a rush origionally.
 
I have now reinstalled it with a 70G partition(ext3) and a 7G swap space partition. Its seems to be running well and I am no longer short of disk space.
 
I appreciate the time, im from a HW background and SW is still a bit alien to me!
cheers
a

---

