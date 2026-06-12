---
title: "Ubuntu not booting after installation... Windows booting directly"
date: 2010-03-13
forum: New to Ubuntu
---

### Post by Sampath.T.J on 2010-03-13
I'm new to linux n ubuntu... i installed ubuntu 9.10... The installation completed without any errors and asked for rebooting... but wen it rebooted it directly starts windows xp... i have 2 hard drives one 160gb n one 250 gb... windows is on d 160gb drive while i've allocated a part of d 250gb drive for ubuntu.. i did manual partitioning... wen i boot from ubuntu live cd i can see d ubuntu installation.. wen i tried F8 during boot also it shows xp as d only OS... 
Any help is appreciated... and could u pls explain things in layman's language?? as i told u i'm new to ubuntu.... thnx in advance...

---

### Post by Elfy on 2010-03-13
Did you install ubuntu directly or is it a wubi install (that is inside windows) ?

Can you boot the livecd and then open a terminal from the apps > accessories menu and run this

```
sudo fdisk -l
```

post the output here please.

---

### Post by Sampath.T.J on 2010-03-13
i installed it from d live cd directly... i mean at boot up...

i ran d code... should i post wat it displayed or something????

---

### Post by Sampath.T.J on 2010-03-13
here's d output....

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x17361736

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6527    52428096    7  HPFS/NTFS
/dev/sda2            6528        6588      489982+  82  Linux swap / Solaris
/dev/sda3   *        6589       13054    51938145   83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04190418

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2432    19535008+   7  HPFS/NTFS
/dev/sdb2            2433       19457   136753312+   f  W95 Ext'd (LBA)
/dev/sdb5            2433        6688    34186288+   b  W95 FAT32
/dev/sdb6            6689       10944    34186288+   b  W95 FAT32
/dev/sdb7           10945       15200    34186288+   b  W95 FAT32
/dev/sdb8           15201       19457    34194321    b  W95 FAT32

Disk /dev/sdc: 8027 MB, 8027897856 bytes
5 heads, 32 sectors/track, 97996 cylinders
Units = cylinders of 160 * 512 = 81920 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          51       97997     7835712    c  W95 FAT32 (LBA)

---

### Post by Sampath.T.J on 2010-03-13
Help needed.. pls...

---

### Post by eriktheblu on 2010-03-13
Go into your BIOS, find the boot device priority, set the 250 GB (Ubuntu) disk above the 160 GB (Windows) disk.

Each disk has a master boot record that points to the boot partition. Your BIOS looks for boot devices in order (typically CD first then hard drive). It goes to the first device available, in this case your Windows disk.

---

### Post by Sampath.T.J on 2010-03-13
hmm.. i did try changing it yest but it was not changing... i'll try it out once again l8r 2day... thank u....

---

### Post by _h_ on 2010-03-13
> **Sampath.T.J said:**
> hmm.. i did try changing it yest but it was not changing... i'll try it out once again l8r 2day... thank u....

Make sure when you make those changes and goto exit the BIOS you select SAVE and EXIT option, and not just a regular exit.

---

### Post by Sampath.T.J on 2010-03-13
no i meant dat it wasnt changing itself.... not after exiting...

---

### Post by Sampath.T.J on 2010-03-13
anyways i'll try it out now.... n let u kno...

---

### Post by msidhard on 2010-03-13
Sampath just download super grub disk and burn the thing in new cd. Then boot the system from super grub disk. Then install grub in hd0.  Or follow the instructions in that cd. Where are you from

---

### Post by eriktheblu on 2010-03-13
In my BIOS there a basic list of optical, USB, floppy, HDD, and network boot. To identify priority between multiple optical and HDDs I actually need to go to a more advanced mode where I can identify the disks individually.

Another alternative:
You might repartition your 160GB disk to add a small (~256MB should work) /boot partition for Grub. This would obviously not be the preferred method.

---

### Post by Sampath.T.J on 2010-03-13
m frm bangalore... thanx for ur info... however d prev solution worked perfectly fine....

[eriktheblu]("http://ubuntuforums.org/member.php?u=508854"), [_h_]("http://ubuntuforums.org/member.php?u=1033713"), [[COLOR=#D40000]**forestpiskie**[/COLOR]]("http://ubuntuforums.org/member.php?u=610428")... thanx to all u guys...

---

### Post by souleke on 2010-03-13
at the ubuntu to the materboot of windows 
i believe (correct me if i'm wrong) its in your boot.ini 
you need to at the boot of ubuntu in there, not so easy to do 
(i dont own or like windows so can help you on that sry)

the better way is to install grub into to masterboot record of the windows hd
and at the windows part to the list 
grub can handle windows and linux boot without any prbleme

you can install the grub with the live cd 
here is the how to: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
install grub on (hd0,0)
try to boot 
it can be windows will already show up in the list (in this case your ready and will have a dual boot on your system)
if not 
you need to add the windows partition to the grub loader 
it woud be something like this 

```
title MS Windows XP <-- change with name of your windows 
root (hd0,0) <--- the numbers are 
                        /dev/sda1 == (hd0,0) (your showing fdisk -l i geuss its (hd0,0) 
                        /dev/sdb1 == (hd1,0) 
savedefault 
makeactive 
chainloader +1 


```boot into your ubuntu and edit /boot/grub/menu.lst
```
sudo gedit /boot/grub/menu.lst 
```dont change anything just add the lines below and save 
reboot and select the windows see if it boots, if not you need the set the right partion
(hd0,0) is wrong, try next one 

please search for info on boot options before you try; there can be a easy way from windows i don't know ;-)

---

### Post by sailor2001 on 2010-03-13
in terminal: sudo gedit /boot/grub/menu.lst ....default should be 0 for ubuntu and counting up from there would be recovery mode (1) then memtest (2), other operating systems (3) xp (4) etc......  Boot loader is installed (grub) automatically on ubuntu installation.  if not using wubi

---

