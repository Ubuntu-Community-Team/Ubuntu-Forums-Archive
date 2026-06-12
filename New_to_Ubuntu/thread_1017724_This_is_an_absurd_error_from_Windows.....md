---
title: "This is an absurd error from Windows...."
date: 2008-12-21
forum: New to Ubuntu
---

### Post by ajeetraj on 2008-12-21
I just installed intrepid (linux mint) by using a usb stick and it worked perfectly fine on my duel boot laptop. I have been using duel boot since I got this laptop. After my intrepid install, now when I try to boot windows I get the following error: 

Windows could not start because of the following file is missing or corrupt. 
<windows root>\system32\hal.dll
Please reinstall a copy of the above file. 

I looked around the internet and I found that to fix this problem I will have to use the windows CD, which I don't have it anymore. I was wondering if Intrepid messed up my hdd in anyway and now I can't boot into Windows. 

Can anyone help me with this please?

I will greatly appreciate any help. 

Thanks!

---

### Post by bumanie on 2008-12-21
The error you are getting indicates the partition number of where windows is residing and the partition number as recorded in boot.ini are different. post thet output of > sudo fdisk -land confirm whether you can mount the windows partition from within ubuntu or not, just becasue it won't boot, doesn't mean that it's files can't be seen from within ubuntu.

---

### Post by ajeetraj on 2008-12-21
I don't know how to mount it manually now but this is the output of the command you gave me. 

```
deepu@newleaf ~ $ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         244     1959898+  82  Linux swap / Solaris
/dev/sda2             245        1275     8281507+   5  Extended
/dev/sda3            1276        4430    25342537+  83  Linux
/dev/sda4   *        4431        7296    23021145    7  HPFS/NTFS
/dev/sda5             245        1275     8281476   83  Linux
deepu@newleaf ~ $ 

```

Thanks!

---

### Post by anjilslaire on 2008-12-21
hal.dll is usually something that may not be simply copied from the install disc, as hal.dll is in some cases unique to each install. Reinstalling Windows may be needed.

---

### Post by ajeetraj on 2008-12-21
ah that's a bummer. So there is no other way? Another reason why Windows should not be installed on any of the damn computers in the whole world. 

bastards!

---

### Post by bumanie on 2008-12-21
You have the same issue as another poster who repartitioned his drive and has ended up with windows inside an extended partition - windows does not like this at all. Where was windows prior to the installation of ubuntu? I think it would have been on the first partition of the drive, which is why the number recorded in boot.ini and the partition number windows is on no longer match. This is the most common cause of this error partition numbers getting changed. What anjilslaire says could also be right, but as you have patitioned the drive recently the boot.ini problem is the most likely cause. Do you have an external hard drive large enough to copy windows to?

---

### Post by ajeetraj on 2008-12-21
Yes I do have a large external hdd where I can copy the files but I don't know how to mount the windows partition.

---

### Post by ugm6hr on 2008-12-21
Look at this: [http://support.microsoft.com/kb/945380/](http://support.microsoft.com/kb/945380/)

This generally represents a corrupt system directory / file.

Sometimes, it is a hardware problem - make sure your files are backed up, then run a diagnostic on your HD.

---

