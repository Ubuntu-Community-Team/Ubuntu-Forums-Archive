---
title: "How to find local disk not configured during xubuntu installation"
date: 2011-01-04
forum: New to Ubuntu
---

### Post by Cafargo on 2011-01-04
Hello all.

This is xubuntu 9.04. My old P2 box has two disks (4.7g each). One of the disks (I suspect the slave) was not configured/mounted during the installation procedure (I must have been gone to get my coffee at that point ;)). Of course, I cannot mount the 2nd disk as it cannot be found/detected. Is there a way of detecting the so-called missing disk, so I can obtain the necessary information in order to mount it (e.g. commands, scripts, etc.)? Or, must I simply re-install xubuntu and follow instructions more attentively. 
Any help would be greatly appreciated. And there is no rush, I'm in no hurry.

Many thanks.
Pierre.

---

### Post by cheapie on 2011-01-04
Can you post the output of "ls /dev"?

---

### Post by oldos2er on 2011-01-04
Is the disk listed under the Places menu? Can you post the output of **sudo fdisk -l** ?

---

### Post by gmargo on 2011-01-04
You might try the **blkid(8)** program.  With no arguments it will search for disks.

---

### Post by Cafargo on 2011-01-04
Hello Everyone.

Thanks for your replies. Here are the results from ls /dev and sudo fdisk -l:

pierre@ubuntu:~$ ls /dev
agpgart          net                 random    tty14  tty40  ttyS0
block            network_latency     rtc       tty15  tty41  ttyS1
bus              network_throughput  rtc0      tty16  tty42  ttyS2
cdrom            null                scd0      tty17  tty43  ttyS3
char             nvidia0             sda       tty18  tty44  urandom
console          nvidiactl           sda1      tty19  tty45  usbdev1.1_ep00
core             oldmem              sda2      tty2   tty46  usbdev1.1_ep81
cpu_dma_latency  pktcdvd             sda5      tty20  tty47  usbmon0
disk             port                sdb       tty21  tty48  usbmon1
ecryptfs         ppp                 sdb1      tty22  tty49  vcs
fd               psaux               sdb2      tty23  tty5   vcs1
full             ptmx                sdb5      tty24  tty50  vcs2
fuse             pts                 sg0       tty25  tty51  vcs3
initctl          ram0                sg1       tty26  tty52  vcs4
input            ram1                sg2       tty27  tty53  vcs5
kmem             ram10               shm       tty28  tty54  vcs6
kmsg             ram11               snapshot  tty29  tty55  vcs7
log              ram12               sndstat   tty3   tty56  vcs8
loop0            ram13               sr0       tty30  tty57  vcsa
loop1            ram14               stderr    tty31  tty58  vcsa1
loop2            ram15               stdin     tty32  tty59  vcsa2
loop3            ram2                stdout    tty33  tty6   vcsa3
loop4            ram3                tty       tty34  tty60  vcsa4
loop5            ram4                tty0      tty35  tty61  vcsa5
loop6            ram5                tty1      tty36  tty62  vcsa6
loop7            ram6                tty10     tty37  tty63  vcsa7
MAKEDEV          ram7                tty11     tty38  tty7   vcsa8
mapper           ram8                tty12     tty39  tty8   xconsole
mem              ram9                tty13     tty4   tty9   zero
pierre@ubuntu:~$ sudo fdisk -l
[sudo] password for pierre: 

Disk /dev/sda: 4320 MB, 4320862208 bytes
255 heads, 63 sectors/track, 525 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7b706929

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         495     3976056   83  Linux
/dev/sda2             496         525      240975    5  Extended
/dev/sda5             496         525      240943+  82  Linux swap / Solaris

Disk /dev/sdb: 4320 MB, 4320862208 bytes
255 heads, 63 sectors/track, 525 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7b70692a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         495     3976056   83  Linux
/dev/sdb2             496         525      240975    5  Extended
/dev/sdb5             496         525      240943+  82  Linux swap / Solaris
pierre@ubuntu:~$ 
_______________________________

I will investigate the blkid (8) program. Where does one find it?

Many thanks!
Pierre

---

### Post by Cafargo on 2011-01-04
This is more like it. Sorry for the mess in the previous post:


[HTML]pierre@ubuntu:~$ ls /dev
agpgart          net                 random    tty14  tty40  ttyS0
block            network_latency     rtc       tty15  tty41  ttyS1
bus              network_throughput  rtc0      tty16  tty42  ttyS2
cdrom            null                scd0      tty17  tty43  ttyS3
char             nvidia0             sda       tty18  tty44  urandom
console          nvidiactl           sda1      tty19  tty45  usbdev1.1_ep00
core             oldmem              sda2      tty2   tty46  usbdev1.1_ep81
cpu_dma_latency  pktcdvd             sda5      tty20  tty47  usbmon0
disk             port                sdb       tty21  tty48  usbmon1
ecryptfs         ppp                 sdb1      tty22  tty49  vcs
fd               psaux               sdb2      tty23  tty5   vcs1
full             ptmx                sdb5      tty24  tty50  vcs2
fuse             pts                 sg0       tty25  tty51  vcs3
initctl          ram0                sg1       tty26  tty52  vcs4
input            ram1                sg2       tty27  tty53  vcs5
kmem             ram10               shm       tty28  tty54  vcs6
kmsg             ram11               snapshot  tty29  tty55  vcs7
log              ram12               sndstat   tty3   tty56  vcs8
loop0            ram13               sr0       tty30  tty57  vcsa
loop1            ram14               stderr    tty31  tty58  vcsa1
loop2            ram15               stdin     tty32  tty59  vcsa2
loop3            ram2                stdout    tty33  tty6   vcsa3
loop4            ram3                tty       tty34  tty60  vcsa4
loop5            ram4                tty0      tty35  tty61  vcsa5
loop6            ram5                tty1      tty36  tty62  vcsa6
loop7            ram6                tty10     tty37  tty63  vcsa7
MAKEDEV          ram7                tty11     tty38  tty7   vcsa8
mapper           ram8                tty12     tty39  tty8   xconsole
mem              ram9                tty13     tty4   tty9   zero
pierre@ubuntu:~$ sudo fdisk -l
[sudo] password for pierre: 

Disk /dev/sda: 4320 MB, 4320862208 bytes
255 heads, 63 sectors/track, 525 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7b706929

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         495     3976056   83  Linux
/dev/sda2             496         525      240975    5  Extended
/dev/sda5             496         525      240943+  82  Linux swap / Solaris

Disk /dev/sdb: 4320 MB, 4320862208 bytes
255 heads, 63 sectors/track, 525 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7b70692a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         495     3976056   83  Linux
/dev/sdb2             496         525      240975    5  Extended
/dev/sdb5             496         525      240943+  82  Linux swap / Solaris
pierre@ubuntu:~$ 
[/HTML]

---

### Post by Cafargo on 2011-01-04
Here are the results of sudo blkid

[HTML]pierre@ubuntu:~$ sudo blkid
/dev/sda1: UUID="ea54f20e-02b7-4360-bbf7-d9fc9c32224c" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="a40493ae-462a-426c-a413-d4c842f42e50" 
/dev/sdb1: UUID="30cdf37b-1659-40d3-a607-9717673a3ccf" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="7ccf87ca-3b39-4a9a-ae2e-485556195d5d" 
pierre@ubuntu:~$ 
[/HTML]

So, this verbose indicates one filesystem with the swaps. Would sdb1 be my 2nd disk? 

Cheers,
P.

---

### Post by blind2314 on 2011-01-04
Yes, sdb1 is a partition (or slice) on your second physical disk.

---

### Post by Cafargo on 2011-01-05
How do I make it come to life? I added the sdb1 line in my fstab, but I gather there is some crucial information missing after the UUID. I'm also not sure about the 'ext' number, I put 2. Maybe I'm out to lunch on that one. Any suggestions would help. Many thanks!:

[HTML]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ea54f20e-02b7-4360-bbf7-d9fc9c32224c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=a40493ae-462a-426c-a413-d4c842f42e50 none            swap    sw              0       0
# /dev/sdb1
UUID="30cdf37b-1659-40d3-a607-9717673a3ccf /		  ext2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0[/HTML]

---

### Post by Cafargo on 2011-01-05
Oops, sorry. I failed to mention that I did indeed mount sdba1, but results from df -k show that sda1 and sdb1 have the identical stats as far as blocks, used, etc... which makes me suspicious that it's not my 2nd disk, but in fact sda1. So, I wonder what went wrong.

Thanks,
Pierre

---

### Post by blind2314 on 2011-01-05
That's because you're trying to mount both disks to /..that won't work. Create a separate directory under / to mount your second disk too, such as ```
mkdir /myseconddisk
``` or something clever.

---

### Post by Cafargo on 2011-01-05
Here's the df -k print out:

[HTML]pierre@ubuntu:~$ df -k
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1              3913496   2919396    795300  79% /
tmpfs                   254756         0    254756   0% /lib/init/rw
varrun                  254756       104    254652   1% /var/run
varlock                 254756         0    254756   0% /var/lock
udev                    254756       156    254600   1% /dev
tmpfs                   254756         0    254756   0% /dev/shm
lrm                     254756      2192    252564   1% /lib/modules/2.6.28-19-generic/volatile
/dev/sdb1              3913496   2919396    795300  79% /
[/HTML]

---

### Post by Cafargo on 2011-01-06
Okay, great. It now works fine. I totally forgot about creating the mount folder.

Many thanks Blind2314!!!

---

