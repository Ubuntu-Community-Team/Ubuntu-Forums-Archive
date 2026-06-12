---
title: "File system very small,  how can I enlarge it"
date: 2009-10-10
forum: New to Ubuntu
---

### Post by knowledgestudent on 2009-10-10
Hi there, 
I am very beginner to ubuntu, 
I have installed it beside windows XP, and took the default of partitioning options " side by side "; I have four partitions C for windows and the other 3 are all of size 75 G, only the D has some data , 

after I installed the ubuntu, I have checked the file system size and found the free is only 48 MB, actually I need to install ns2( network simulator) but the size of file system caused me issues , I know that I can install the ubuntu again and take the partitioning manually, but I thought that there could be some way to resize (enlarge) the partition as we could in windows, instead of re-doing every thing agian !!!!!!

any suggestions please , help is appreciated
Tahnks in advance 
Best Regards, 
knowledgestudent

---

### Post by superdav42 on 2009-10-10
See [resizing ext partitions]("http://www.howtoforge.com/linux_resizing_ext3_partitions") For how you can enlarge your linux partition without loosing data. But first see which fs is so small. Do ```
df -h
```

---

### Post by knowledgestudent on 2009-10-10
Thank for your fast reply :) appreciated , 
this is the result of the df -h : 

Filesystem            Size  Used Avail Use% Mounted on

/dev/sda8             2.3G  2.2G   37M  99% /

tmpfs                 972M     0  972M   0% /lib/init/rw

varrun                972M  112K  972M   1% /var/run

varlock               972M     0  972M   0% /var/lock

udev                  972M  184K  972M   1% /dev

tmpfs                 972M  104K  972M   1% /dev/shm

lrm                   972M  2.4M  970M   1% /lib/modules/2.6.28-11-generic/volatile

/dev/sda7              73G   70M   72G   1% /media/disk

/dev/sr0              137M  137M     0 100% /media/cdrom0

/dev/sda6              75G   73M   75G   1% /media/disk-1

/dev/sda5              75G   14G   61G  19% /media/disk-2


hope that I can solve this issue with out re-installing again

---

### Post by cariboo on 2009-10-10
I would suggest you use gparted to resize your partition. From the looks of your listing it looks like /dev/sda7 ohly has 70Mb used, you could take some space from that partition for /dev/sda8. Gparted is in on the Live CD, boot from it to resize your partitions. Look for Partition Editor under System-->Administration.

My standard install takes about 4Gb, so I would suggest at least a 10Gb partiton for a linux installation.

---

### Post by knowledgestudent on 2009-10-11
Hi, 
I have installed the Gparted, and when I tried to enlarge my file system, I found that the problem actually that all of the drive is formatted as NTFS!!!, so that I had to delete the logical drive then formated it again as an ext3, I did not continue with that track as I did not remember what are files on windows drivers,

so that here is a note for who are going to install ubuntu while they have the windows already installed, u need to make an appropriate part of the disk, (that fits your requirements), deleted (delete the logical partition from windows disk manager for example), then when you install the ubuntu, when you come to the partitioning part ( do not be afraid :P ) and choose the advanced partitioning, you will see a list of svailable disks, and there will be the unpartitioned disk , there u can partition it as you need, and do not forget to make the mount (/), so that the file system take the main path 
good Luck :)

---

### Post by 3rdalbum on 2009-10-11
> **knowledgestudent said:**
> so that here is a note for who are going to install ubuntu while they have the windows already installed, u need to make an appropriate part of the disk, (that fits your requirements), deleted (delete the logical partition from windows disk manager for example), then when you install the ubuntu, when you come to the partitioning part ( do not be afraid :P ) and choose the advanced partitioning, you will see a list of svailable disks, and there will be the unpartitioned disk , there u can partition it as you need, and do not forget to make the mount (/), so that the file system take the main path 
good Luck :)

Or you can use the "resize a partition" option, and make sure you move the little slider towards the left side. Look carefully at the bottom bar graph - the little slider is on the right.

---

