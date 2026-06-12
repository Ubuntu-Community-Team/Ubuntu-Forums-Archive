---
title: "PartImage"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by mesmith on 2009-01-29
I would like to use partimage to backup one hdd partition to another.  I have two hdd's sda and sdb.  I want to copy sda1 to sdb1.  I need to know a couple of things about using the rescuecd which I have burned.  Before invoking partimage do I have to mount /media/sdb1 as my target device, or is mounting automatic?  I do have both my source and target hdd's in /dev as /dev/sda1 and sdb1.  I set a prior mountpoint at /media/sdb1 and this mounts automatically (normally) because I am using Storage Device Manager, which will not have been invoked since I'm booting off a cd. I have never edited fstab and don't want to if possible.

Thanks in advance.

---

### Post by wirelessmonkey on 2009-01-29
you don't mount the destination partition....  and you must have a volume mounted on which to store the image and restore from.

---

### Post by mesmith on 2009-01-29
I'm sorry.  A newbie here.  I don't have to mount the partion, but I do have to mount the hdd?  I don't understand.  I should mount sdb after the rescue disk boots, but before I open partimage?  Something like:  mount /dev/sdb /media/sdb?  Sorry if things are not clear to me.  After mounthing the hdd I would choose a target partition like /media/sdb1/somename?

Thanks.

---

### Post by bumanie on 2009-01-29
If you want a direct clone, I usually use dd commands such as > dd if=/dev/sda of=/dev/sdbThat will cause a byte to byte copy from sda to sdb
if = input file
of = output file

Unless you want it compressed or something, it is that simple to clone one hard drive to another. Partimage is basically a GUI on top of dd. If you choose to use dd, it is best to do it from a live cd, because the filesystem you are copying needs to be unmounted otherwise a consistent output cannot be guaranteed. You can double check your partition names by using code > cat /proc/partitionsin terminal from the live cd.

---

### Post by wirelessmonkey on 2009-01-30
I'll give you a quick walkthrough of how I do a partimage.

Assuming you've rebooted into the rescuecd...
Partimage creates an image file of the partition you wish to copy.  You must have a place to put that image, before restoring it to the second drive.

In this example I'll use sdc1, though it can be a network drive, or another partition on sda or sdb, so long as there is enough space for the image.

so, after booting the rescue disk..

```
mount /dev/sdc1 /mnt/custom
partimage -b -g0 -z1 save /dev/sda1 /mnt/custom/myimage.000

```
 
This will create your disk image.  You then want to restore the image to sdb1
```
partimage -g0 restore /mnt/custom/myimage.000 /dev/sdb1 
```




edit:  dd does sound like a better option for you in this situation, but if you do have a place to store a partimage, it's much less space intensive than dd, and a compressed partimage is a great backup.

---

### Post by mesmith on 2009-01-30
I get it.  You create an image file, then restore it to the target partition.  In my case, the target hdd is smaller than the source, but still just big enough.  Some compression would help.

Where can I find out what all those "-" parameters correspond to?  Do any of them relate to compression?  Medium compression would be fine, I think.  Would I then put a .gz at the end of my target file name?  Or perhaps the image file name?

I was using the gui, and it seemed to be doing this job in one pass, i.e. source to target, period.  Perhaps I misunderstood that after image creation there would be another pass to restore.  I got the feeling that the image creation might be taking place without my intervention or instructions.

Thanks again.

---

### Post by mesmith on 2009-02-01
Thanks for all your help.  Ended up making a directory in /mnt, then mounting the target drive.  Used the gui and all went perfectly.

Thanks again.

---

### Post by mesmith on 2009-02-03
Running a simple linux system with two hdd's. Drive one has two partitions - linux plus swap. Hdd two a single partition. Both Ext3.

I successfully created an image of my primary partition onto disk 2.

My assumtion was that if ever suffer total hdd failure on disk one, I would be able to buy a new hdd. Partition it, format it and then restore the primary partition from the second hdd. The new hdd would likely be larger than the second, but if that caused any trouble the partition size could be adjusted after the restore.

This seemed like a simple process. However, I have come across lots of web based chatter about MBR's and Partition tables that have me baffled. Do I need to know about these things with my system and application of partimage?

---

### Post by mesmith on 2009-02-07
As luck would have it, after building an image file on my second drive I had a terrible crash on my primary partion on drive one.  I had no choice but to use the rescue disk and have a go at restoring my primary partition.  I'm happy to report that it worked perfectly.  In ten minutes I had a restored partition and was back on the air.

---

