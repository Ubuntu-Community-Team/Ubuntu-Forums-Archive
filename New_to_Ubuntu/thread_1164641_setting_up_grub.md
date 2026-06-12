---
title: "setting up grub"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by shadow120 on 2009-05-19
i'm running 9.04 on my first hard drive,  i installed 9.10 on a second hard drive and got grub error 22 i fixed from the live cd but now i dont get the option to load 9.10.  how do i set up grub to do this? i tried googling this but i all i found were dual booting windows or dual booting from the same hard drive.  so any help would be apriciated

edit: when i installed 9.10 i set up grub on the mbr of the first hard drive if that helps

---

### Post by louieb on 2009-05-19
When I need grub help this is where I go [IDBS GRUB Page ]("http://users.bigpond.net.au/hermanzone/p15.htm")
Look for the chainload or configfile statment. Both a good for loading diffrent linux installs.

---

### Post by presence1960 on 2009-05-19
> **shadow120 said:**
> i'm running 9.04 on my first hard drive,  i installed 9.10 on a second hard drive and got grub error 22 i fixed from the live cd but now i dont get the option to load 9.10.  how do i set up grub to do this? i tried googling this but i all i found were dual booting windows or dual booting from the same hard drive.  so any help would be apriciated

edit: when i installed 9.10 i set up grub on the mbr of the first hard drive if that helps

do you mean 8.10 on your 2nd hard drive? I will assume this. Edit your menu.lst file on the 9.04 partition by adding this after ### End Debian Automagic Kernels List

```
# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

title           Intrepid 8.10
rootnoverify    (hd1,x)
chainloader     +1
```
 
where x is the partition of your 8.10 install. Remember GRUB counts the first partition as 0 (zero). 


I say this without seeing how your setup actually is. if it doesn't work download this script to your desktop: [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

Then open a terminal and run : > sudo bash ~/Desktop/boot_info_script*.sh

this will create a RESULTS.txt file on your desktop which contains your system setup & boot info. Paste the contents of the file here. Highlight the text and click the # sign on the toolbar of the message box.

---

### Post by shadow120 on 2009-05-19
ok i think im close.  ive edited my /boot/grub/menu.lst file and added to the end of it

```
title		ubuntu 9.10 
root		(hd1,0)
makeactive
chainloader	+1
```

now it shows up in the grub menu at start up but i keep geting error 21 i have tried 
(hd1,0)
(hd1,1)
(hd2,0)
(hd2,1)
what am i doing wrong.  here is what i get when i run fdisk -l
```

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4660    37431418+  83  Linux
/dev/sda2            4661        4865     1646662+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 20.4 GB, 20419854336 bytes
255 heads, 63 sectors/track, 2482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x31353439

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2373    19061091   83  Linux
/dev/sdb2            2374        2482      875542+   5  Extended
/dev/sdb5            2374        2482      875511   82  Linux swap / Solaris

```

any help would be appreciated

---

### Post by presence1960 on 2009-05-19
I don't see a boot flag on partition sdb1. I have Kubuntu 9.04 installed on sdb2. Note the asterisk in the boot column for sdb2. This may be your problem.

here is my fdisk -l
```

raz@raz-desktop:~$ sudo fdisk -l
[sudo] password for raz: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000d179

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20972826    7  HPFS/NTFS
/dev/sda2            2612        4569    15727635   83  Linux
/dev/sda3            4570       29879   203302575   83  Linux
/dev/sda4           29880       30401     4192965   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa7a57e45

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       16477   132351471   83  Linux
/dev/sdb2   *       16478       18389    15358140   83  Linux
/dev/sdb3           18390       19457     8578710    7  HPFS/NTFS
```

---

### Post by louieb on 2009-05-20
to make this work 
```
title        ubuntu 9.10 
root        (hd1,0)
makeactive
chainloader    +1
```

1st you must install grub stage1 in the boot sector of the partition

at the **grub> **prompt.

```
root (hd1,0)
setup (hd1,0)
quit
```

its all explained in the link I gave earlier. Good Luck.

---

