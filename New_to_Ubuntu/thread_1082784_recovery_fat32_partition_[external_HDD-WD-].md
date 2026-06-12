---
title: "recovery fat32 partition [external HDD-WD-]"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by redmorning on 2009-02-28
hi folks,

you may think title is too similar,i googled around this topic too much but i can't find a good solution (which is step-by-step) and this isa pretty senstive.i tried testdisk but couldn't finish the job without a good guide.

my first problem is;

when i was changing some partition size with gparted one process took pretty long -about 3 hours- so i left my computer,because of something  -still couldn't figure out- my laptop shutdown and after that i could only see lost+found folder. this partition -ext3- is 69.7 gb totally and 44.7 gb used (still seems same in system monitor) but in file browser when i look at its properties it's 18.4 gb and all my files -except lost+found folder- are gone.

to solve this problem i decided to copy this partition to my external hdd -WD- before starting to use recovery tools,so i typed

sudo dd if=/dev/sda5 of=/dev/sdb1

/sda5 : my lost partition
/sdb1 : fat32 partition in HDD with 455 gb

problem 2 ;

i realized my mistake after 24 s and 600 mb of data was already copied and now i can't access anything in My Book. i guess all my files are now in mode overwritten,i screwed up i know and there is no undo of this command of course..
i spoke with some companies of recovery and it will cost between 150-250 $ for one disk.

i thougt that i can buy a new HDD (1 tb) with that money and make my own recovery -i need some space to copy my entire /sdb1- but i can't be that brave enough without any experience,if someone can help me to save my money and handle this by myself i will be preciated,thanks

batu

---

### Post by taurus on 2009-02-28
Not sure if this will fix your problem but at least give TestDisk a try.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by redmorning on 2009-02-28
thank you for this fast reply taurus,

now i'm gonna read all stuff but i also need some confirmation and experience of people who saved their data with this or another program..

thanks..

---

### Post by caljohnsmith on 2009-02-28
How about first posting:
```
sudo fdisk -lu
```
Also, I agree with Taurus that testdisk is an excellent tool to start with to see if it might possibly be able to recover your partition; in order to use testdisk, how about downloading the [testdisk-6.10.linux26.tar.bz2]("http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2") package to your desktop, and then do:
```

cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static /dev/sdb1
```
After starting testdisk, choose "Proceed", "None", "Analyze", "Quick Search", then press "p" to see if testdisk can give you a directory listing of the root file system. Let me know if that returns anything or if it gives you an error.

---

### Post by redmorning on 2009-02-28
thanks,

i can't do those steps tonight,but i will let you know about those informations tomorrow.

---

### Post by redmorning on 2009-03-02
piratejackus@gemi:~$ sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd4243518

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63      289169      144553+  83  Linux
/dev/sda2          289170    29639924    14675377+  83  Linux
/dev/sda3        29639925   168345134    69352605   83  Linux
/dev/sda4       168345135   234436544    33045705    5  Extended
/dev/sda5       168345198   178209044     4931923+  83  Linux
/dev/sda6       178209108   229070834    25430863+  83  Linux
/dev/sda7       229070898   234436544     2682823+  82  Linux swap / Solaris

Disk /dev/sdb: 1010 MB, 1010826752 bytes
255 heads, 63 sectors/track, 122 cylinders, total 1974271 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x91f72d24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     1974270      987104    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(121, 254, 63) logical=(122, 227, 40)

 here what you want caljohnsmith,i decided to first try recovery of a usb -1 gb- with testdisk,i copied some files in it -about 890 mb- then i copied boot folder -with 86 mb- in it by the command 

sudo dd if=/dev/sda1 of=/dev/sdb1

just like the previous time,command created some files which are unreadable and unexecutable,if i can save my files in this usb -except 86 mb of it- i'm gonna try it with my 500 gb.so i start.

now 

sudo testdisk-6.10/linux/testdisk_static /dev/sdb1

"Proceed", "None", "Analyze", "Quick Search", then "p" DONE

now i can see the files which i overwrote -/boot files- copied them to my desktop and can read them now but coludn't list my old files,after "deepre search" just reached my laptop partitions.

failed,i need more help and courage..

thanks anyway..

---

### Post by redmorning on 2009-03-02
piratejackus@gemi:~$ sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd4243518

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63      289169      144553+  83  Linux
/dev/sda2          289170    29639924    14675377+  83  Linux
/dev/sda3        29639925   168345134    69352605   83  Linux
/dev/sda4       168345135   234436544    33045705    5  Extended
/dev/sda5       168345198   178209044     4931923+  83  Linux
/dev/sda6       178209108   229070834    25430863+  83  Linux
/dev/sda7       229070898   234436544     2682823+  82  Linux swap / Solaris

Disk /dev/sdb: 1010 MB, 1010826752 bytes
255 heads, 63 sectors/track, 122 cylinders, total 1974271 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x91f72d24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     1974270      987104    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(121, 254, 63) logical=(122, 227, 40)

 here what you want caljohnsmith,i decided to first try recovery of a usb -1 gb- with testdisk,i copied some files in it -about 890 mb- then i copied boot folder -with 86 mb- in it by the command 

sudo dd if=/dev/sda1 of=/dev/sdb1

just like the previous time,command created some files which are unreadable and unexecutable,if i can save my files in this usb -except 86 mb of it- i'm gonna try it with my 500 gb.so i start.

now 

sudo testdisk-6.10/linux/testdisk_static /dev/sdb1

"Proceed", "None", "Analyze", "Quick Search", then "p" DONE

now i can see the files which i overwrote -/boot files- copied them to my desktop and can read them now but coludn't list my old files,after "deeper search" just reached my laptop partitions.

failed,i need more help and courage..

thanks anyway..

---

### Post by redmorning on 2009-03-02
i must add that in all the sectors - / -
No file found,filesystem seems damaged.

---

### Post by caljohnsmith on 2009-03-02
I don't understand what you were doing, because you said originally that you accidentally overwrote part of your sdb1 partition on your 455 GB WD HDD with that dd command; when you did the fdisk command, it did not show a 455 GB HDD, only your 120 GB sda drive and a 1 GB flash drive. Where is your 455 GB HDD, and is that the drive you are trying to recover the partition on?

---

### Post by redmorning on 2009-03-02
i am at the university for the day,i tried testdisk on 1 gb disk for test like i said,tonight i'm gonna mount mh 455 gb disk and send you fdisk output again.

in the other hand can you help me to figure out why i can't recover my data from usb which i have overwrote it a little,i don't think that there will be a big difference because i used same command,the only difference is the capacity of the disk.am i wrong?

---

