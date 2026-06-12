---
title: "how to add windows hard drive to grub?"
date: 2010-02-09
forum: New to Ubuntu
---

### Post by fwin on 2010-02-09
Hi,

I have two hard drives in my desktop one with ubuntu (master) and the other one with windows xp (slave). I can not boot the windows drive and I already tried to add the code shown below to the  menu.lst file. With this code windows is shown on the grub list but it gives me an error message and it does not boot

title Windows XP
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd0,0)
chainloader +1


Here is the result of "fdisk -l"

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3d209eb4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9638    77417203+  83  Linux
/dev/sda2            9639        9729      730957+   5  Extended
/dev/sda5            9639        9729      730926   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd2fcd2fc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4862    39053983+   7  HPFS/NTFS



I would really appreciate any help.

---

### Post by egalvan on 2010-02-09
> **fwin said:**
> Hi,
I have two hard drives in my desktop one with ubuntu (master) and the other one with windows xp (slave).
 **I can not boot the windows drive **and I already tried to add the code shown below to the  menu.lst file.

Did it ever work? Is this a new problem?
Or has it never worked?

>  With this code windows is shown on the grub list but **it gives me an error message **and it does not boot


What is the EXACT code you receive?

---

### Post by fwin on 2010-02-09
egalvan,

thanks for replying, here are the answers to your questions:

-No, it has never worked, it is the first time i am trying to do this.

-this is the error that i receive:

     Error 13: Invalid or unsupported executable format
         
      Press any key to continue....

After pressing any key it goes back to the grub list.

---

### Post by fwin on 2010-02-09
Since i could not figure out what was happening i decided to install ubuntu 9.10 from a flash drive instead of upgrading from 9.04. This time the windows xp option was shown in the grub list, but when I select that option windows won't boot, i get a grub error saying that it cant find c/h/s values. 

How can i make windows boot from grub?, please help  :confused:

---

### Post by oldfred on 2010-02-09
grub can only boot a working windows. If you put the windows drive as master will it boot? If not you need to use your windows cd to repair the windows install.

---

### Post by fwin on 2010-02-09
thanks for replying oldfred, but i just solved the problem by going to the BIOS and turning on the slave hard drive, it was set to OFF.

For the record:

-Turning on the windows hd (slave) in the BIOS did not work when i had the ubuntu 9.10 that i got from upgrading 9.04.

-The solution was to install the 9.10 version from a flash drive while the windows hd (slave) was connected. After that I turned on the slave hd in the BIOS.

-My computer is a DELL OPTIPLEX G270.

Thanks to everyone for your help.

---

