---
title: "[SOLVED] Swap @ 0%"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by technomensch on 2008-12-29
I feel like I've done something wrong.

I've got one HDD with 4 partitions:

```
$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2c74badc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5052    40580158+  27  Unknown
/dev/sda2            5053        7011    15735667+   5  Extended
/dev/sda3            7012       14593    60902415    7  HPFS/NTFS
/dev/sda5            5053        5545     3959991   82  Linux swap / Solaris
/dev/sda6            5546        7011    11775613+  83  Linux
```

/sda1 = Vista Installation
/sda3 = NTFS data storage
/sda5 = swap
/sda6 = ext3 Ubuntu installation

I was using "pysdm" to get sda1 and sda3 to mount on boot.  Of course I would forget to make a backup of my original fstab prior to making any changes.  Here's what I have so far:

```
$ more /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults 
                                             0  0  
#/dev/sda6                                  UUID=c051e299-c001-4d25-a147-a4adf52
a6e7a  /              ext3         relatime,errors=remount-ro                   
         0  1  
#/dev/sda5                                  UUID=1f08be22-c3cc-45b9-8603-a0cfe73
71b0c  none           swap         sw                                           
         0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noau
to,exec,utf8                                 0  0  
/dev/sda6                                  /media/sda6    ext3         defaults 
                                             0  0  
/dev/sda5 none swap sw 0 0
#/dev/sda5                                  /media/sda5    swap         sw      
                                              0  0  
/dev/sda3                                  /media/DATA    ntfs         nls=iso88
59-1,users,umask=000,user,owner,uid=user  0  0  
/dev/sda1                                  /media/ACER    ntfs         nls=iso88
59-1,users,umask=000,user,owner,uid=user  0  0
```

For some reason, my CPU screenlet is showing that my swap is using 0% even with several windows of Firefox, Thunderbird, Screenlets, Google Gadgets, and Google Desktop running.

```
$ free -t -m
             total       used       free     shared    buffers     cached
Mem:          1755       1600        154          0         74        538
-/+ buffers/cache:        987        768
Swap:         3867          2       3865
Total:        5623       1603       4020
```

htop finally just started to show 2MB being used, but it's still hovering around 0:

```

$ free -t -m
             total       used       free     shared    buffers     cached
Mem:          1755       1600        154          0         74        538
-/+ buffers/cache:        987        768
Swap:         3867          2       3865
Total:        5623       1603       4020
```

```
top - 21:58:57 up 58 min,  3 users,  load average: 1.58, 0.97, 0.81
Tasks: 153 total,   1 running, 152 sleeping,   0 stopped,   0 zombie
Cpu(s): 20.7%us,  4.6%sy,  1.2%ni, 69.9%id,  3.3%wa,  0.1%hi,  0.1%si,  0.0%st
Mem:   1798080k total,  1640444k used,   157636k free,    76592k buffers
Swap:  3959980k total,     2140k used,  3957840k free,   551900k cached
```

```
$ vmstat
procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 3  0   2140 155996  76748 552516    0    0    87   100  341  815 22  5 70  3
```

Already tried:

```
% sudo swapoff -a && sudo swapon -a 
```

No Errors

```
% sudo vol_id -u /dev/sda1
e464f53c-06ff-4c71-b589-a370911a9d33
```

*Is there any other way to confirm that my swap is actually working?  OR...If I broke it, what might have broke and how to fix it?*

---

### Post by HereInOz on 2008-12-29
If you look at the output of free, you will find that indeed you have a swap of 3867 MB with 2MB used, so I would reckon that your system is seeing the swap partition and is using it as needed.  

If you really want to test it, reduce your on-board RAM to 256MB and then watch your swap partition usage.  It is not uncommon, with 1.8GB of RAM, that the swap will not get used much at all, unless you start using virtual machines and things like that.

---

### Post by bgerlich on 2008-12-29
It's working fine. It will be a big simplification but swapping memory pages works like this: you add half the percentage of used memory, number of times the kernel had to free up memory in some period and the value of constant vm.swappiness (default 60). If the value of the addition is more than 100 the kernel will start swapping. Apparently yours isn't.

---

### Post by sdennie on 2008-12-29
I would consider 0% swap usage fairly normal if you have more than 1G of RAM.  If you are coming from Windows, you will find that linux handles memory a bit differently.  You can make it use swap more aggressively if you want but, the default setting is generally good for most people.  The setting that controls how aggressively the kernel uses swap is in /etc/sysctl.conf and called vm.swappiness.  Setting it to a high value (i.e. 100) will make the machine use more swap while setting it low (i.e. 0) will make the machine almost never use swap.  The default setting in recent kernels is 60.

---

### Post by technomensch on 2008-12-29
Normally I'd agree with you, but I had seen the swap being used in both htop and the screenlet prior to making the mounting modifications.  That's what has me confused and thrown off.

---

### Post by sdennie on 2008-12-29
If "free -m" is listing swap and even showing some of it used, you can be absolutely certain that your swap partition is mounted properly.

---

### Post by bgerlich on 2008-12-29
As one of the previous posters said - if you really want to test your swap space you can crank up vm.swappiness setting to 100 (sudo sysctl -w vm.swappiness=100). You won't see the change instantly, you have to do some memory intensive operations. Opening few huge images in GIMP will do the trick.

---

### Post by igknighted on 2008-12-29
> **technomensch said:**
> Normally I'd agree with you, but I had seen the swap being used in both htop and the screenlet prior to making the mounting modifications.  That's what has me confused and thrown off.

Not using swap is definitely a good thing.  Imagine swap as really, really slow ram that will bog the system down.  It's great as a backup if you absolutely need it, but in normal use, it'll really slow you down if the system tries to use it.

---

