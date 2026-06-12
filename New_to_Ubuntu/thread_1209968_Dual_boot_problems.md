---
title: "Dual boot problems"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by kirk_m on 2009-07-10
Hi,

Last week, I installed Ubuntu 9.04 x64 onto a computer which already had Windows XP pro 64.  All installed fine, and, upon rebooting the machine, I was given the option to boot into linux or into windows by GRUB.  Booting into linux works fine, but, booting into windows doesn't work.  It doesn't give me an error code or anything, but just says "Starting Up..."  and just sits there, never loading windows.   How would I go about fixing it?

**Results of cat /boot/grub/device.map:**
 
(hd0)    /dev/sda
(hd1)    /dev/sdb
(hd2)    /dev/sdc
(hd3)    /dev/sdd
(hd4)    /dev/sdf
(hd5)    /dev/sdh

**At the end of the /boot/grub/menu.lst:**

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title        Windows XP Professional x64 Edition
map        (hd0) (hd2)
map        (hd2) (hd0)
rootnoverify    (hd2,0)
makeactive
savedefault
chainloader    +1

**Fdisk -l results:**

sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c559d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14593   117218241    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x57ca3c80

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       33434   268558573+   7  HPFS/NTFS
/dev/sdb2           33435       38913    44010067+   5  Extended
/dev/sdb5           33435       38783    42965811   83  Linux
/dev/sdb6           38784       38913     1044193+  83  Linux

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f8000b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9119    73248336    7  HPFS/NTFS
/dev/sdc2            9120        9729     4899825    5  Extended
/dev/sdc5            9120        9605     3903763+  83  Linux
/dev/sdc6            9606        9729      995998+  82  Linux swap / Solaris


Any help appreciated...

Thanks,

Kirk

---

### Post by LewRockwell on 2009-07-10
where is your windows? which drive and which partition?

.

---

### Post by kirk_m on 2009-07-11
Lew,

It is on /dev/sdc partition /dev/sdc1

Thanks,

Kirk

---

### Post by LewRockwell on 2009-07-11
Windows doesn't play well with others and wants to be on the FIRST drive(boot drive) AND first partition

as you can see from your menu.lst grub is attempting to use "map" to fool windoze into believing it is where it wants to be

typically(and to avoid such problems) we normally attempt to put the "doze" where it is most "behaved" as opposed to the screams from the back forty

you might get Supergrubdisk and see if that will fix things up for you

it takes some effort and there is a learning curve to it's many usages and if you have any questions you can always ask

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

and, as always, if you can't afford to lose it forever...back it up...

keep us posted!

.

---

