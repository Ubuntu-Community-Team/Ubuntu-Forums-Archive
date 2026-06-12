---
title: "File names change from Windows to ubuntu"
date: 2009-08-06
forum: New to Ubuntu
---

### Post by josnygaa on 2009-08-06
When I copy a file from WinXP to ubuntu which contain non-English characters (on a Samba share), the 'foreign' characters change to _ (underscore).

E.g. the file 'løpere.txt' changes name to 'l_pere.txt'. If I make a file with these characters in ubuntu, the same problem applies when I copy the file to Windows.

As a NOOB, I am not able to figure this out, even after hours on different forums. I have learnt that this might have something to do with different character sets and mounting of partitions, but I simply can't work it out.


My partition table:

Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe2d6e2d6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4676    37559938+  83  Linux
/dev/sda2            4677        4863     1502077+   5  Extended
/dev/sda5            4677        4863     1502046   82  Linux swap / Solaris


My fstab looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=cc90e7a4-d7ba-4d79-aa7e-37ee83e54f4b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=a48325ad-499a-427c-8b99-cb1c1c76db4a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

I have set language settings in System - Administration - Language Support to Norwegian (nb_NO).

I think I have to change something in the fstab file, but I do not know what.

Can someone please help?

---

### Post by egalvan on 2009-08-06
I remember reading a short "how-to" by one of the Forum staff,
on how to mount Japanese file names on Samba.

Unfortunately, I don't remember anything else about it,
since at that time I had no interest in either Japanese file names, 
nor Samba, :confused:

Maybe someone with a better memory will pipe in.

---

### Post by josnygaa on 2009-08-07
Thanks for your info, egalvan. I will try and search for it. Anyone else using ubuntu with other languages than English with Samba? Please.

---

### Post by josnygaa on 2009-08-07
I finally found the answer to my character problems. I got some good ideas from this thread: [http://ubuntuforums.org/showthread.php?t=1080511](http://ubuntuforums.org/showthread.php?t=1080511)

I added this line to the end of my fstab (using: gksudo gedit /etc/fstab):

/dev/sda1       /media/sda1     ntfs-3g  defaults,locale=nb_NO.UTF-8  0  0

I also created a directory for the mount (I don't know if this is necessary):

sudo mkdir /media/sda1

I can now use æ ø å in filenames without losing information. Case solved!

---

