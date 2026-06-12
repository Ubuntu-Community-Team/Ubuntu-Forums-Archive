---
title: "Hard Drive repair tool"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by ozbolt on 2009-02-10
I have empty half-working discs (I don't know which one of 3 works and which one has a problem). So I am searching for a Linux distro that would do one big check for bad sectors and stuff like this and "repair tool" would be perfect. 
Thanks for any suggenstions.
I am not familliar with shell (terminal), so if that is only way please a quick guide.

Thanks anybody for help.

---

### Post by mkvnmtr on 2009-02-10
There is a site that lists all the live disks. You will need to google linux live disks. Several of these are rescue or repair disks. You will need to go to the home pages of the ones that look like they have what you need to find out if indeed they can help you and how to use them. a regular desctop disk will probably not have the tools you need.

---

### Post by cariboo on 2009-02-10
If you have the LiveCD you can boot from it. once at the desktop open a Applications-->Accessories-->Termianl and type:

```
sudo e2fsck -fpC 0 /dev/sdXY
```

/dev/sdXY= the device label of the hard drive. IF you aren't sure what the device labels are before running the above command type in the same terminal:

```
sudo fdisk -l
```

the result should be something like this:

```
164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00066acc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       20023   160834716   83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x51b6cc16

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       10199    81922048    7  HPFS/NTFS
/dev/sdb2           10200       10964     6144862+  83  Linux
/dev/sdb3           10965       11474     4096575   82  Linux swap / Solaris
/dev/sdb4           11475       30401   152031127+  83  Linux
```

The device labels are at the start of each line. As you can see I have two hard drives, one with 1 partition and 1 with 4 partitions.

Jim

---

### Post by lkraemer on 2009-02-12
I'd suggest that you look at the drives names and then go to the
maufacturer's site and download their diagnostic tools.  Run them
on the drive first. Another option is to use something like Spinrite
on each of the drives after you have done the OEM Diagnostics.
Spinrite isn't free but it is worth the money if you really need it.
(I am not sure it works with SATA, but their website should say.)
Google Spinrite.

You might also check out:
UBCD (Ultimate Boot CD)
System Rescue CD.

lkraemer

---

### Post by Bablefish on 2009-02-12
If you don't mind paying for the program this is honestly the best tool I know period [http://www.grc.com/sr/spinrite.htm](http://www.grc.com/sr/spinrite.htm)

---

