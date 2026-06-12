---
title: "[SOLVED] Unable to delete files from an infected USB drive"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by LastWho on 2008-12-05
Hi,
i m not able to delete files (or to paste new ones) from an Usb drive, that is infected with viruses; 

[INDENT]**- permissions:**
[/INDENT] > ~$ ll /media/ZINX/
total 55M
drwx------ 12 ucef root  16K 1970-01-01 00:00 ./
-rwx------  1 ucef root  24K 2007-07-06 21:01 **[COLOR=Teal]Funky sms.mp3[/COLOR]***
dr-x------ 10 ucef root  32K 2008-07-31 21:47 [COLOR=RoyalBlue]**pb**[/COLOR]/
drwx------ 22 ucef root  16K 2008-07-31 21:47 [COLOR=RoyalBlue]**lifeblog**[/COLOR]/
drwx------ 15 ucef root  16K 2008-07-31 21:47 **[COLOR=RoyalBlue]Private[/COLOR]**/
drwx------  5 ucef root  16K 2008-07-31 21:49 [COLOR=RoyalBlue]**Images**[/COLOR]/
drwx------  5 ucef root  16K 2008-07-31 21:49 [COLOR=RoyalBlue]**Videos**[/COLOR]/
drwx------ 18 ucef root  16K 2008-07-31 21:49 [COLOR=RoyalBlue]**Sounds**[/COLOR]/
-rwx------  1 ucef root 4.0K 2008-11-28 21:20 **[COLOR=Teal]@samsung.ess*[/COLOR]**
drwx------  2 ucef root  16K 2008-11-28 21:20 [COLOR=RoyalBlue]**Other files/**[/COLOR]
drwx------  3 ucef root  16K 2008-11-28 21:20**[COLOR=RoyalBlue] Music[/COLOR]**/
drwx------  3 ucef root  16K 2008-11-28 21:37 [COLOR=RoyalBlue]**.Trash-1000/**[/COLOR]
-rwx------  1 ucef root  54M 2008-11-28 23:01 **[COLOR=Teal]002.mp3*[/COLOR]**
-rwx------  1 ucef root 641K 2008-11-28 23:01 [COLOR=Teal]**12.mp3***[/COLOR]
-rwx------  1 ucef root    0 2008-11-28 23:01 [COLOR=Teal]**15_heart.mp3***[/COLOR]
drwx------  2 ucef root  16K 2008-12-03 17:56 **[COLOR=Teal]kjhk/[/COLOR]**
drwxr-xr-x  6 root root 4.0K 2008-12-05 13:20 ../

(ps: ll is "ls -Flarth")

[INDENT][B]
- [/B]i tried to use **gdparted:** but i got this error message
[/INDENT]
> gksudo gparted /media/ZINX/
======================
libparted : 1.7.1
======================
Unable to open /media/ZINX read-write (Is a directory).  /media/ZINX has been opened read-only.
Unable to open /media/ZINX read-write (Is a directory).  /media/ZINX has been opened read-only.
Unable to open /media/ZINX - unrecognised disk label.

what should i do please?
thx

---

### Post by taurus on 2008-12-05
Do you want to reformat the drive?  And when you use gparted, you need to include the device name, something like /dev/sdb1, not the mount point.  Otherwise, just run gparted by itself.

```
gksudo gparted
```

---

### Post by LastWho on 2008-12-05
yes, i want to reformat the drive (if that ll help me to get it clean and use it again), can u tell me please plz how could i know the dev name?
because when i run gparted alone it shows me only 3 partitions:
/dev/sda1 --> ext3 /home
/dev/sda2 --> ext3 /
/dev/sda3 --> linux-swap 

(the usb drive is mounted, and i can read from it)

---

### Post by newbee70 on 2008-12-05
> **taurus said:**
> Do you want to reformat the drive?  And when you use gparted, you need to include the device name, something like /dev/sdb1, not the mount point.  Otherwise, just run gparted by itself.

```
gksudo gparted
```

check your drive location with:

Sudo fisk -l 

-l = small L not 1

it will give you something like this:


Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d5d32

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30213   242685891   83  Linux
/dev/sda2           30214       30401     1510110    5  Extended
/dev/sda5           30214       30401     1510078+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00035a17

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30213   242685891    7  HPFS/NTFS
/dev/sdb2           30214       30401     1510110    5  Extended
/dev/sdb5           30214       30401     1510078+  82  Linux swap / Solaris

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5c74ae42

location of my external drive = /dev/sdc1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001    7  HPFS/NTFS
wohoo@hooters:~$

---

### Post by taurus on 2008-12-05
If you want to reformat the drive, you first need to unmount it.

```
sudo umount /media/ZINX
```
Then, fire up gparted and browse to that drive.  Then, format it from there.

---

### Post by newbee70 on 2008-12-05
> **taurus said:**
> If you want to reformat the drive, you first need to unmount it.

```
sudo umount /media/ZINX
```
Then, fire up gparted and browse to that drive.  Then, format it from there.

Thanks; taught me a good lesson read all posts twice before putting foot in mouth;then read the third time for accuracy. I missed the post where he had it still mounted. And I missed the connection that he had already listed his directory on the drive.

---

### Post by taurus on 2008-12-05
> **newbee70 said:**
> Thanks; taught me a good lesson read all posts twice before putting foot in mouth;then read the third time for accuracy. I missed the post where he had it still mounted. And I missed the connection that he had already listed his directory on the drive.

I wouldn't worry too much about it.  You were just trying to help.

---

### Post by LastWho on 2008-12-05
thanks for ur help,
but still i m not able to find the drive using gparted, here what i got:
> 
~$ sudo umount /media/ZINX/
~$ gksudo gparted
======================
libparted : 1.7.1
======================
Unable to open /dev/sdf - unrecognised disk label.

then gdparted shows me only the three partions:
sda1 (/home), sda2 (/), sda3 (swap)

@Newbee 70: thx but:
> ~$ sudo fisk -l
sudo: fisk: command not found

~$ fisk -l
bash: fisk: command not found


---

### Post by taurus on 2008-12-05
Can you post the output of this command?

```
sudo fdisk -l
```
What filesystem do you want to format that USB drive?

---

### Post by LastWho on 2008-12-05
> **taurus said:**
> Can you post the output of this command?

```
sudo fdisk -l
```
What filesystem do you want to format that USB drive?
thank u lol now i got it :p

this is my usb drive:
```
Disk /dev/sdb: 1014 MB, 1014497280 bytes
28 heads, 27 sectors/track, 2620 cylinders
Units = cylinders of 756 * 512 = 387072 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2621      990594+   6  FAT16

```

and:
```
gksudo gparted /dev/sdb
```
then i formated it to Fat32 (i hope its not a wrong thing)

then:
```
Disk /dev/sdb: 1014 MB, 1014497280 bytes
28 heads, 27 sectors/track, 2620 cylinders
Units = cylinders of 756 * 512 = 387072 bytes
Disk identifier: 0x000cb5fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2621      990594+   b  W95 FAT32

```

i think evrything is ok now, thank you so much taurus and Newbee 70 :popcorn:

---

