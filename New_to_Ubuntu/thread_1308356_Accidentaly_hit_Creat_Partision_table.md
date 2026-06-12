---
title: "Accidentaly hit Creat Partision table"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by dagarshali on 2009-10-31
Hi,
I have installed the new 9.10. I was running out of space..so I went to the widows partition and shrunk the volume. I then came to ubuntu and using gparted i made that volume into ext3. I then accidentally hit the creat partision table. I couldn't cancel it..Now, when i restart the computer, I get an error 22 in the grub load. I have some pretty important data in the disk.. I am not sure what I have done.. 

could anyboby please help me fix this problem...

regards,
vishwa

---

### Post by jrrader on 2009-10-31
It is possible to recover files after formatting, but I do not know how yet.  What I do know is that it is important that you do not do anything to the partition until you find out how.  If you write anything onto that partition you reduce your chances of getting your files off of it.

---

### Post by dagarshali on 2009-10-31
I haven't done anything since the error came..i just used a live cd to see if can do something about this grub error 22..

when i do sudo fdisk -l this is the output i get

ubuntu@ubuntu:~$ sudo fdisk -l

> Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8e0eee9e

   Device Boot      Start         End      Blocks   Id  System


and when i hit sudo grub..

Then find /boot/grub/menu.lst, i get this
Error 15: File not found


Any help..PLEASE...

---

### Post by LewRockwell on 2009-10-31
you can try the Parted Magic LiveCD Utilities Disk

[http://partedmagic.com/](http://partedmagic.com/)

you will probably want to use Testdisk to see if you can recover your partitions

.

---

### Post by dagarshali on 2009-10-31
thanks for getting back to me..

How will i use the test disk..right now i am using a live cd for 8.04lts even though i have installed 9.10. 

i have internet connection thru wireless..do i need to install testdisk or it is already available? 

Regards,
Vishwa

---

### Post by LewRockwell on 2009-10-31
> **dagarshali said:**
> right now i am using a live cd for 8.04lts even though i have installed 9.10. 

i have internet connection thru wireless..do i need to install testdisk or it is already available?

download partedmagic from [http://partedmagic.com/](http://partedmagic.com/)

burn to disk

run as LiveCD and use Testdisk

[http://en.wikipedia.org/wiki/TestDisk](http://en.wikipedia.org/wiki/TestDisk)

.

---

### Post by dagarshali on 2009-10-31
Hi, I downloaded partedmagic like you suggested..

when i ran testdisk. it said in one of the screens ( the screen which lists partition) that no bootable partitions found. i am analyzing it and not sure what the outcome will be.

when i rand the partition editor. it open saying there is 298gb of disk and it is unallocated..:(

does it mean i have lost all the data.. all i did was click a creat partition table thing by accident..:(

Regards,
Vishwa

---

### Post by dagarshali on 2009-10-31
Hi All,
I ran the testdisk using partedmagic disk and i am posting the output..

> TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 320 GB / 298 GiB - CHS 38914 255 63
     Partition               Start        End    Size in sectors
D FAT32 LBA                0   1  1 33002 254 63  530193132 [NO NAME]
D HPFS - NTFS              0  32 33 21939  13 42  352448848
D HPFS - NTFS              0  32 33 33002 177  7  530186240
D HPFS - NTFS              0  32 45 32676 254 63  524953945
D Linux                21940   0  1 23854 254 60   30764472
D Linux                23855   1  1 32485 254 63  138656952
D Linux                28158   0  1 36788 253 63  138656952
D Linux Swap           32486   1  1 33001 254 42    8289456
D Linux                32677   2  1 32980 254 61    4883632
D Linux Swap           32981   1  1 33001 254 41     337280
D HPFS - NTFS          33002 209 40 36987  37 42   64008192 [LENOVO]
* HPFS - NTFS          36987  37 43 38899 129 14   30722048





Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
FAT32, 271 GB / 252 GiB

Now I am seeing that the D in front of say Linux means deleted..what do i do next..?

Regards,
Vishwa

---

### Post by cariboo on 2009-10-31
If you have an external drive, you can use photorec, which is part of the testdisk package to recover your missing files and copy them to another drive.

---

### Post by dagarshali on 2009-10-31
could i just not restore the partition table... are you saying that i will have to back this data up and reinstall the ubuntu..?

Regards,
Vishwa

---

### Post by dagarshali on 2009-11-01
Hi,
the result of running the testdisk utility is as shown below.

How do I decide which one amongst these are *, P, L and E..

thanks,
vishwa

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 320 GB / 298 GiB - CHS 38914 255 63
Partition Start End Size in sectors
D FAT32 LBA 0 1 1 33002 254 63 530193132 [NO NAME]
D HPFS - NTFS 0 32 33 21939 13 42 352448848
D HPFS - NTFS 0 32 33 33002 177 7 530186240
D HPFS - NTFS 0 32 45 32676 254 63 524953945
D Linux 21940 0 1 23854 254 60 30764472
D Linux 23855 1 1 32485 254 63 138656952
D Linux 28158 0 1 36788 253 63 138656952
D Linux Swap 32486 1 1 33001 254 42 8289456
D Linux 32677 2 1 32980 254 61 4883632
D Linux Swap 32981 1 1 33001 254 41 337280
D HPFS - NTFS 33002 209 40 36987 37 42 64008192 [LENOVO]
* HPFS - NTFS 36987 37 43 38899 129 14 30722048





Structure: Ok. Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable P=Primary L=Logical E=Extended D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
Enter: to continue
FAT32, 271 GB / 252 GiB

---

### Post by sandyd on 2009-11-01
nvm.

---

### Post by sandyd on 2009-11-01
> **dagarshali said:**
> Hi,
the result of running the testdisk utility is as shown below.

How do I decide which one amongst these are *, P, L and E..

thanks,
vishwa

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 320 GB / 298 GiB - CHS 38914 255 63
Partition Start End Size in sectors
D FAT32 LBA 0 1 1 33002 254 63 530193132 [NO NAME]
D HPFS - NTFS 0 32 33 21939 13 42 352448848
D HPFS - NTFS 0 32 33 33002 177 7 530186240
D HPFS - NTFS 0 32 45 32676 254 63 524953945
D Linux 21940 0 1 23854 254 60 30764472
D Linux 23855 1 1 32485 254 63 138656952
D Linux 28158 0 1 36788 253 63 138656952
D Linux Swap 32486 1 1 33001 254 42 8289456
D Linux 32677 2 1 32980 254 61 4883632
D Linux Swap 32981 1 1 33001 254 41 337280
D HPFS - NTFS 33002 209 40 36987 37 42 64008192 [LENOVO]
* HPFS - NTFS 36987 37 43 38899 129 14 30722048





Structure: Ok. Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable P=Primary L=Logical E=Extended D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
Enter: to continue
FAT32, 271 GB / 252 GiB
says in the front. the only * partition you have is at the buttom.
the rest shows "D" which means you deleted them.

although i would guess that one of these
```

D Linux 23855 1 1 32485 254 63 138656952
D Linux 28158 0 1 36788 253 63 138656952
```
is your main partition. judging from the amount of space that is.

---

### Post by LewRockwell on 2009-11-01
good day mates!

[http://www.howtoforge.com/data_recovery_with_testdisk](http://www.howtoforge.com/data_recovery_with_testdisk)

[http://digg.com/linux_unix/Recover_deleted_partitions_using_Testdisk_in_Ubuntu](http://digg.com/linux_unix/Recover_deleted_partitions_using_Testdisk_in_Ubuntu)

.

---

### Post by dagarshali on 2009-11-01
Hi,
I did look up the video and read the article on digg.com.. Since I am new to linux, I am not sure which partition here to be selected as P, L, * etc..

I have windows vista installed as well and I boot using Grub.. The linux in on the partition which is 66GB..the drive which says lenovo, contains drivers and things like that..

Regards,
Vishwa

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>


Disk /dev/sda - 320 GB / 298 GiB - CHS 38914 255 63
Partition Start End Size in sectors
D FAT32 LBA 0 1 1 33002 254 63 530193132 [NO NAME]
D HPFS - NTFS 0 32 33 21939 13 42 352448848
D HPFS - NTFS 0 32 33 33002 177 7 530186240
D HPFS - NTFS 0 32 45 32676 254 63 524953945
**When i select the above partition and type p to list files, i get the message that I can't open file**
D Linux 21940 0 1 23854 254 60 30764472
D Linux 23855 1 1 32485 254 63 138656952
D Linux 28158 0 1 36788 253 63 138656952
**can't open the above either**
D Linux Swap 32486 1 1 33001 254 42 8289456
D Linux 32677 2 1 32980 254 61 4883632
D Linux Swap 32981 1 1 33001 254 41 337280
D HPFS - NTFS 33002 209 40 36987 37 42 64008192 [LENOVO]
* HPFS - NTFS 36987 37 43 38899 129 14 30722048





Structure: Ok. Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable P=Primary L=Logical E=Extended D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
Enter: to continue
FAT32, 271 GB / 252 GiB

---

