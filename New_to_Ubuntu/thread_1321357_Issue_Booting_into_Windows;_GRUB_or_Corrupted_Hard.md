---
title: "Issue Booting into Windows; GRUB or Corrupted Hard Drive?"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by cheph on 2009-11-10
Hi,

I have windows vista loaded on my internal laptop hard drive and ubuntu 9.04 on my usb external hard drive. I GRUB loaded on the external and have been using this setup for around 6 months now. I am a casual user and am so completely familiar with technical things of linux. My friend has been advising me on how to fix my issue but now we are both stuck.

my "fdisk -l" result is :

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7       14201   114021337+   7  HPFS/NTFS
/dev/sda3           14202       14593     3148740    f  W95 Ext'd (LBA)
/dev/sda5           14202       14593     3148708+  dd  Unknown

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00038216

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3891    31250000   82  Linux swap / Solaris
/dev/sdb2            3892       91201   701317575   83  Linux


When I would take my external hard drive out, and try boot windows I would get a grub 21 error. I tried to move my grub loader off the external using

"grub-install /dev/sda2"

I later realisied my mistake and tried to move grub back.

While I can still boot into Ubuntu, now I cannot mount my Windows hard drive OR boot into windows. When I select Windows from the grub menu, it just refreshes and doesn't boot.

I have previously had problems with my internal hard drive so I am not sure if it is a grub problem or if my hard drive is now corrupt.

I was advised to install "ntfsprogs" and use "testdisk" to check my ntfs windows hard drive. We followed this for reference: [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

During testdisk:

Partitions visible:

Disk /dev/sda - 120 GB / 111 GiB - CHS 14593 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 P Dell Utility             0   1  1     5 254 63      96327
 2 * HPFS - NTFS              6   0  1 14200 254 63  228042675
 3 E extended LBA         14201   0  1 14592 254 63    6297480
 5 L Sys=DD               14201   1  1 14592 254 63    6297417


When I selected to "Analyse" the NTF partition I got;

Disk /dev/sda - 120 GB / 111 GiB - CHS 14594 255 63
     Partition               Start        End    Size in sectors
* FAT16 >32M               0   1  1     5 254 63      96327 [DellUtility]
P HPFS - NTFS              6   0  1 14200 254 63  228042675
L FAT32 LBA            14201   1  1 14592 254 63    6297417 [MEDIADIRECT]



Finally When i did "Deep Search", I got the message:

Disk /dev/sda - 120 GB / 111 GiB - CHS 14594 255 63

The harddisk (120 GB / 111 GiB) seems too small! (< 1889353 TB / 1718356 TiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partition can't be recovered:
     Partition               Start        End    Size in sectors
  HFS                   9627 114 24 2067506516 106 22 1355421312



I am now not sure what to do. I am also not sure if what I have done so far is correct. Any ideas on where to go from here would be much appreciated!!


Thanks,

cheph

---

### Post by kansasnoob on 2009-11-10
Is 111 GB of 120 GB really used on the Windows drive?

That alone is not good, but when you installed grub to sda2 you probably really hosed some of the Windows boot files.

---

### Post by cheph on 2009-11-10
ya man its all used, thats another story though. I have been considering doing a BIOS diagnostic test but am not sure if that will be helpful?

Cheph

---

### Post by Bucky Ball on 2009-11-10
Open a terminal (Applications->Accessories->Terminal) and paste this in:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```That makes a copy of your /boot/grub/menu.lst file in case something screws up (which it shouldn't). Now this:
```

nano /boot/grub/menu.lst 
```That lets you look at the menu.lst file and get aquainted but you can't change anything. Look for a Windows entry in that file near the bottom that looks something like this:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windoze
root            (hd0,0)
savedefault
makeactive
chainloader     +1

# This is a divider, added to separate the menu items below from the Debian
# ones.
```Yours should look like this:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windoze
[B]root            (hd0,1)
map           (hd0,1) (hd0,0)
map            (hd0,0) (hd0,1)[/B]
savedefault
makeactive
chainloader     +1

# This is a divider, added to separate the menu items below from the Debian
# ones.
```You need to change what I have in bold. Did that work?

When you are confident of what you need to do, hit ctl+X and get back to the cursor then paste:

```
sudo nano /boot/grub/menu.lst
```Now you have opened the file as root and your changes will stick. Change and add the section I have marked in bold. Good luck.

---

### Post by cheph on 2009-11-10
hey man, thanks for the reply

I tried what you said the original was this

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows Vista/Longhorn (loader)
root            (hd0,1)
savedefault
makeactive
chainloader     +1


then I changed it to this

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows Vista/Longhorn (loader)
root            (hd0,1)
map           (hd0,1) (hd0,0)
map            (hd0,0) (hd0,1)
savedefault
makeactive
chainloader     +1

I rebooted but still could not get windows to load. I have not changed the menu list back yet, i figured it couldn't hurt.

cheph

---

### Post by Bucky Ball on 2009-11-10
Did you get the same error or a different one?

---

### Post by cheph on 2009-11-10
same

---

### Post by oldfred on 2009-11-10
When you installed grub to sda2 which is your window partition you overwrote the windows boot that is in the windows partition. you have to run the fixboot to rewrite the windows boot in the partition.

presence does a better job of explaining the details, see his post here for the same issue:
[http://ubuntuforums.org/showthread.php?t=1319880](http://ubuntuforums.org/showthread.php?t=1319880)

---

### Post by Bucky Ball on 2009-11-10
Pretty easy. If you have a Windows install CD, boot from it go to 'Repair'. When you hit the cursor there run these three commands:

chkdisk
fixmbr
fixboot

That's it.

---

### Post by cheph on 2009-11-10
WOW, thanks a lot guys that worked like a charm, I can boot vista again! I still cant boot vista without my external hard-drive (Ubuntu) plugged in but it was like that before. Everything is back to normal now i can mount the windows partition and everything.

Thanks a lot,
Cheph

---

