---
title: "installation trouble"
date: 2010-03-01
forum: New to Ubuntu
---

### Post by dogpelt on 2010-03-01
I'm an ubuntu virgin and having tried to install it on an old lap-top I find it doesn't recognise my hard drive....
i.e. on start-up I get a message ..
error:no such device:  (long string of numbers and letters)

press any key to continue..
on pressing any key I'm given a screen with several options two of which are memory tests (pass on both)and the other two boot options which loop me back to the error message
Any advice would be greatly appreciated

---

### Post by J V on 2010-03-01
Boot from the live disk and post the output from the terminal of:```
fdisk -l
```

---

### Post by dogpelt on 2010-03-01
I get the following...
fdisk: invalid option -- '1'

usage:fdisk[ -b SSZ] [-u] DISK     change partition table
          fdisk -l [-b SSZ] [-u] DISk  List partition table(s)
          fdisk -s PARTITION            Give partition size(s) in blocks
          fdisk -v                             Give fdisk version  
Here DISK is something like /dev/hdb or dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048  (for certain MO disks ) use 2048 - byte sectors


all of which means very little to me .....seems I have a rather steep learning curve ahead of me

---

### Post by weichimaster on 2010-03-01
> **dogpelt said:**
> I get the following...
fdisk: invalid option -- '1'

usage:fdisk[ -b SSZ] [-u] DISK     change partition table
          fdisk -l [-b SSZ] [-u] DISk  List partition table(s)
          fdisk -s PARTITION            Give partition size(s) in blocks
          fdisk -v                             Give fdisk version  
Here DISK is something like /dev/hdb or dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048  (for certain MO disks ) use 2048 - byte sectors


all of which means very little to me .....seems I have a rather steep learning curve ahead of me

Hi

It's fdisk -l NOT fdisk -1.  (So it's the letter l for lima not the number 1).

---

### Post by dogpelt on 2010-03-02
As I said a steep learning curve ....I'll try again

---

### Post by dogpelt on 2010-03-02
This time I get.....


Disk /dev/sda:40 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
units= 16065 * 512 = 8225280 bytes
Disc identifier: 0x70788a9a


     Device      Boot       Start       End        Blocks        Id          System
/dev/sda1        *              1       4773    38339091       83         Linux
/dev/sda2                    4774     4864        730957+      5          Extended
/dev/sda5                    4774     4864        730926       82         Linux swap / Solaris

---

### Post by dogpelt on 2010-03-02
shameless bump because I really am a bit stuck here

---

### Post by weichimaster on 2010-03-02
The output of the boot script info may be useful.

Boot using a live cd, and follow the instructions on this link:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Post the results, which you can see in the RESULTS.txt file, in this thread. (You should be able to open the file by locating in Nautilus, the file browser, right clicking and choosing the "open with" option. gedit should be one of the options, and it's quite a nice way of viewing the file.)

There's more info on how to use the script here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by dogpelt on 2010-03-04
Thank you all for your help .....I seem to have solved the problem by installing an older version,why this runs and the latest release doesn't I have no idea but I'll experiment and see what happens

---

### Post by pricetech on 2010-03-04
As I understand it, the newer versions leave out support for legacy hardware to keep the size of the installation from ballooning out of control.

Your old laptop probably has some of that legacy hardware in it.

---

