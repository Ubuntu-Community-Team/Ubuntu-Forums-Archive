---
title: "windows partition is gone"
date: 2009-05-28
forum: New to Ubuntu
---

### Post by and1080 on 2009-05-28
Hi everyone,
Until yesterday, I was running a double boot with Ubuntu 9.04 and Windows XP and it was working just fine... until one day I rebooted.
I got the following message when trying to boot ubuntu:
ACPI:Aborted because bad gzip magic numbers
Kernel Panic - not syncing: VFS:Unable to mount root fs on unknown block.
The boot menu was just fine though.
Moreover, win XP wouldn't boot anymore, it would go to dell mediadirect  that I installed long ago whithout ever using it.

Looking at threads, I found a way to get my ubuntu back by doing "update-initramfs -k all -c -v" from an old kernel, and so the lastest version of the kernel works.
The problem now is related with the WinXP partition. It looks like its just gone, I can't access it anywhere. I still can access the dell utility partition, but it doesn't really help.

here is the output from sudo fdsik -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       19132       19457     2618563+   c  W95 FAT32 (LBA)
/dev/sda2           13375       19457    48861697+   5  Extended
/dev/sda5           13375       18241    39094146   83  Linux
/dev/sda6           18242       19457     9767488+  82  Linux swap / Solaris

Partition table entries are not in disk order


my grub file /boot/grub/menu.lst looks fine: here is the end of it:

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1


finally, here is /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=371321f3-782d-4ad9-bc11-4eccb6568d56 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=5ac0cc18-06a6-491a-b02d-271cc984f484 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


Does anyone have any idea where the ntfs partition went? Would there be a way for me to get Windows back without nuking my current install, or at least save the data in the partition before?
Thanks a ton!

---

### Post by Hospadar on 2009-05-28
Well, it looks like it's probably not missing, but maybe corrupted.

Your disk partitions should start at 1 usually

You might try taking a look at the disk in gparted, it can be a little more informative.

Also maybe try running chkdisk from a windows install cd in recovery mode.

Sounds like you probably had some kind of nasty hdd failure that muckied things up.

---

### Post by achase79 on 2009-05-28
can you mount your /dev/sda1 partition?

---

### Post by Canadaxcel24 on 2009-05-28
Did you try manually booting by typing "c" in the grub menu? Any partition trouble I had was fixed by manually specifying the boot file.

---

### Post by JK3mp on 2009-05-28
+1 on the above, then its usually saved in grub entry. Does it just not show up in grub menu at all i assume ??? Or does  it give an error when selecting it...

---

### Post by and1080 on 2009-05-28
Thanks for your answers, guys!
I tried some ideas, and here is what happened:

gparted tells me: "can't have overlapping partitions" and just shows free space

I tried to run chdisk from a windows install CD as well, and I got a blue screen of death not even before the start. I tried twice and then gave up.

I can't mount the /sda1 partition/
~$ mount /sda1
mount: can't find /sda1 in /etc/fstab or /etc/mtab

so, I actually googled the sentence about overlapping partitions and I found someone who pretty much got the same problem as I did: dell media direct was causing problems. I think that when I rebooted I might have hit the dell media direct button (by mistake), and that's what might have caused the trouble.
Anyway, I found this interesting thread:
[http://ubuntuforums.org/archive/index.php/t-961925.html](http://ubuntuforums.org/archive/index.php/t-961925.html)

and I did run testdisk.
it showed the following :

```

Disk /dev/sda - 160 GB / 149 GiB - CHS 19457 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * FAT32 LBA            19131   1  1 19456 254 63    5237127 [MEDIADIRECT]
 2 E extended             13374   0  1 19456 254 63   97723395
Space conflict between the following two partitions
 2 E extended             13374   0  1 19456 254 63   97723395
 1 * FAT32 LBA            19131   1  1 19456 254 63    5237127 [MEDIADIRECT]
 5 L Linux                13374   1  1 18240 254 63   78188292
   X extended             18241   0  1 19456 254 63   19535040
 6 L Linux Swap           18241   1  1 19456 254 63   19534977


*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted


```and here is what a "quick search" showed

```

Disk /dev/sda - 160 GB / 149 GiB - CHS 19457 255 63
     Partition               Start        End    Size in sectors
* HPFS - NTFS              0   1  1 13373 254 63  214853247
L Linux                13374   1  1 18240 254 63   78188292
L Linux Swap           18241   1  1 19456 254 63   19534977

Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
NTFS, 110 GB / 102 GiB

```and then the following:

```

Disk /dev/sda - 160 GB / 149 GiB - CHS 19457 255 63

     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0   1  1 13373 254 63  214853247
 2 E extended LBA         13374   0  1 19456 254 63   97723395
 5 L Linux                13374   1  1 18240 254 63   78188292
 6 L Linux Swap           18241   1  1 19456 254 63   19534977


```I can now decide to write this structure on the disk. I am really not an expert in partitioning, but it looks to me that at least the overlapping will be taken care of. I backed up the data I had on ubuntu. Do you think I should give this a shot? Any ideas?
What scares me is that an extended search shows a lot more partitions with some errors.

---

### Post by Canadaxcel24 on 2009-05-28
If you can write that last partition table, then it seems like it would be worth a try. If you have all of your files backed up, it might be better to format and repartition everything. Nothing like a clean hard drive. Either way, hope everything works out for you!:D

---

