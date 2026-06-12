---
title: "Is my hard drive partitioned correctly?"
date: 2009-07-17
forum: New to Ubuntu
---

### Post by the_king_of_mars on 2009-07-17
I have been receiving various error messages, one in relation to wineservers attempt to install wow, and another through the update manager, each telling me i have to little drive space.

sudo fdisk -l
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59724   479732998+  83  Linux
/dev/sda2           59725       60801     8651002+   5  Extended
/dev/sda5           60051       60801     6032376   82  Linux swap / Solaris
/dev/sda6           59725       60028     2441817   83  Linux
/dev/sda7           60029       60050      176683+  82  Linux swap / Solaris

```

df -h
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             2.3G  2.3G     0 100% /
tmpfs                1007M     0 1007M   0% /lib/init/rw
varrun               1007M  220K 1007M   1% /var/run
varlock              1007M     0 1007M   0% /var/lock
udev                 1007M  152K 1007M   1% /dev
tmpfs                1007M  376K 1006M   1% /dev/shm
lrm                  1007M  2.4M 1004M   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sda1             451G  5.3G  423G   2% /media/sda1
/dev/sr0              657M  657M     0 100% /media/cdrom0

```

Can anyone tell me if these values are normal or if they could be causing my previously mentioned problem. 

Part of my problem is a lack of vocabulary, i have no idea what most of you people are talking about and so must waste several hours trying to phrase a question correctly in google untill i have a solution or know what im talking about. So some kind of dictionary would be helpfull if anyone knows of one. It took me 30 min to figure out what people ment when saying things like "are you root"? its very frustrating.

---

### Post by michy99 on 2009-07-17
2.3G for your main Linux partition is very small. It is full. I would advise expanding it to at least 10G. In the meantime, you might free up some space by running:```
sudo apt-get clean
```

---

### Post by Elfy on 2009-07-17
Have you reinstalled - you appear to have 2 swaps - this is often a result of reinstalling and not removing the old install.

---

### Post by khelben1979 on 2009-07-17
If you're uncertain about Linux partitioning:
[Linux Partition HOWTO]("http://tldp.org/HOWTO/html_single/Partition/#requirements")

I suggest you spend some time reading what it says.

---

### Post by the_king_of_mars on 2009-07-17
> **forestpixie said:**
> Have you reinstalled - you appear to have 2 swaps - this is often a result of reinstalling and not removing the old install.

Yes i have actually, i had several hard drives fail for various reasons yesterday which lead me to believe that my first install didn't work.
Is this a problem?

And im still reading the linux partition howto

---

### Post by Elfy on 2009-07-17
I assume that the first install was on sda1 - it has a lot of space, I would guess that the following install was of the automatic resize type.

As it is you have a lot of free space in the first install and a swap either not being used or unecessary.

Your options are to resize the working install and keep the used swap or to reinstall to the whole disk.

Resizing will entail a bit of moving partitions about too.

The general idea of what needs to be done can be found [http://ubuntuforums.org/showpost.php?p=7632100&postcount=9](http://ubuntuforums.org/showpost.php?p=7632100&postcount=9)

You need to remove sda1 and then resize the extended and then aftermoving sda6 resize it.

If you run ```
cat /etc/fstab
``` you will be able to see which swap you are actually using - it will be either sda5 or sda7 - most likely sda7 - in which case before you move and resize sda6 (which is your current install) you could delete sda5 as well.

Lot of text but once you start with the task it will become fairly intuitive.

Be aware that moving and resizing partitions can take some time and it is as well to have backups of important data.

---

### Post by the_king_of_mars on 2009-07-17
```
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                    0  0  
# / was on /dev/sda6 during installation
UUID=8d6d3faa-506b-45ee-8f05-d9b36a21a55d  /               ext3         relatime,errors=remount-ro  0  1  
# swap was on /dev/sda7 during installation
UUID=89da574d-66c7-4588-b954-8fc4d4d3fbac  none            swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec,utf8    0  0  
/dev/sda1                                  /media/sda1     ext3         errors=remount-ro,users     0  0  
/dev/sda5                                  /media/sda5     swap         defaults                    0  0  
```

Does this mean that im using the 2 smallest partitions as the primary?

---

### Post by lavinog on 2009-07-17
edit: Removed my post. Didn't realize that an hour passed since starting the post

---

### Post by the_king_of_mars on 2009-07-17
Ok so from what ive picked up from your responses and the other thread i was directed too, i need to resize the partition labled /sda6 as that is my system partition, and that information was displayed by the df -h command in the console? The major indicator being this segment;
```
tmpfs                1007M     0 1007M   0% /lib/init/rw
varrun               1007M  220K 1007M   1% /var/run
varlock              1007M     0 1007M   0% /var/lock
udev                 1007M  152K 1007M   1% /dev
tmpfs                1007M  376K 1006M   1% /dev/shm
lrm                  1007M  2.4M 1004M   1% /lib/modules/2.6.28-11-generic/volatile
```

Also does it matter if i use the sda5 swap instead of sda7? Something in the Linux Partition HOWTO that was linked mentioned that a swap towards the end of the drive will function faster.

And should i just set up 2 partitions of equal size in the ext3 format?

---

### Post by lavinog on 2009-07-17
> **the_king_of_mars said:**
> 

Also does it matter if i use the sda5 swap instead of sda7? Something in the Linux Partition HOWTO that was linked mentioned that a swap towards the end of the drive will function faster.
I wouldn't worry about swap speed. It is slow no matter what, and you will rarely see it used if you have plenty of memory. Also harddrives behave in a manner where data doesn't always exist where the file system thinks it does.
It looks like sda5 is 6gigs. You shouldn't need a swap that big if it is.

> 
And should i just set up 2 partitions of equal size in the ext3 format?
What do you hope to gain?

---

### Post by Winlinos on 2009-07-23
For related topic; how do you resize the swap partition??

---

### Post by Elfy on 2009-07-24
> **Winlinos said:**
> For related topic; how do you resize the swap partition??

In a similar manner - but are you sure you need to?

---

