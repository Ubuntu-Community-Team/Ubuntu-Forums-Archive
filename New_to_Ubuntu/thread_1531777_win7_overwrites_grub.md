---
title: "win7 overwrites grub?"
date: 2010-07-15
forum: New to Ubuntu
---

### Post by s.k on 2010-07-15
Guys,

     I somehow get a feeling that this must be old but i couldn't find a right match...

I got a new dell i3  64 bit. I installed ubuntu 10.04 LTS on it  and by default grub gets installed /dev/sda overwriting the MBR. The next time I startup everything runs smoothly if I boot up ubuntu. But if I boot up windows 7 I think win 7 again corrupts the grub on /dev/sda because next time onwards the machine doesn't boot up with a message saying, " No module name found. Press any key to exit." and then " Operating System not found".

Please let me know how i can rectify this so that  i can setup my machine to bootup ubuntu by default and also bootup in win7 when i want to.  

Thanks.

---

### Post by lindsay7 on 2010-07-15
I you can boot into Ubuntu post the results of  sudo fdisk -l  (that is the lower case letter L).

If you can not boot into Ubuntu, boot with the live cd and post the results of sudo fdisk -l

---

### Post by wilee-nilee on 2010-07-15
Take a look at this link and see if it's applicable.
[http://ubuntuforums.org/showpost.php?p=9330849&postcount=9](http://ubuntuforums.org/showpost.php?p=9330849&postcount=9)

---

### Post by s.k on 2010-07-16
Hi Lindsay,

Heres the output from sudo fdisk -l :
____________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          17      136521   de  Dell Utility
/dev/sda2              18        1307    10360832    7  HPFS/NTFS
/dev/sda3   *        1307       66578   524286976    7  HPFS/NTFS
/dev/sda4           66578       77826    90345473    5  Extended
/dev/sda5           66578       67622     8387584   82  Linux swap / Solaris
/dev/sda6           67623       77826    81956864   83  Linux
_______________


let me know what I could do next. Thanks.

---

### Post by s.k on 2010-07-16
Hi Wilee,
   My win 7 re-installation CD is yet to arrive from dell. I guess I will wait for it before I try your suggestions.
Thanks for replying.

---

### Post by wilee-nilee on 2010-07-16
Take a look in the add remove portion of W7 for Dells Data Safe that us probably your problem.

---

### Post by s.k on 2010-07-17
Thanks all, Solved it for now using GRUB legacy. Didn't want to remove dell data safe ( paid $$ u know).  So hope my machine will survive the 3rd reboot. :-)

---

