---
title: "help"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by cowboy7305 on 2009-01-23
**********@ubuntu:~$ hdparm /dev/hdd
/dev/hdd: No such file or directory

Why cant it find this 
trying to run dvd decryptor  on ubunto on windows xp sp3 on a bell insperation530.what i have read is the code that is the first part of this question ,that came from how to put dvd decryptor on ubuntu 
What am i doing wrong, new to this operation system

---

### Post by linuxisevolution on 2009-01-23
> **cowboy7305 said:**
> **********@ubuntu:~$ hdparm /dev/hdd
/dev/hdd: No such file or directory

Why cant it find this 
trying to run dvd decryptor  on ubunto on windows xp sp3 on a bell insperation530.what i have read is the code that is the first part of this question ,that came from how to put dvd decryptor on ubuntu 
What am i doing wrong, new to this operation system


The code is different for each hard drive in your system. But, only the last letter will change ( for hard drives, externals are different...)

for instance, if you want to do this to your first hard drive:

hdparm /dev/hda

or the first partition on your first drive

hdparm /dev/hda1

or second partition on first drive

hdparm /dev/hda2 


The second part of the code, "/dev/hdd" tells what device for hdparm to access. Changing the last 4 or 3 letters changes the device. Type sudo fdisk -l to get a list of your drives. For instance, my output is:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000af8f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       15111   121379076   83  Linux
/dev/sda2   *       15112       17726    21004987+   7  HPFS/NTFS
/dev/sda3           29173       30401     9871942+   5  Extended
/dev/sda4           17727       29172    91939995   83  Linux
/dev/sda5           29173       29209      297171   82  Linux swap / Solaris
/dev/sda6           29210       30401     9574708+  83  Linux

So my first hard drive is /dev/sda, so the command would be hdparm /dev/sda* . I would replace the * with the partition number. If I wanted the second one down ( /dev/sda2 ) then the command would be hdparm /dev/sda2. I think it is /dev/sda on mine and not hda because I have a sata drive. Ide drives should register as hdX.
Good luck. Although, you might be able to find a better alternative to dvd decryption that is easier to install.

---

### Post by linuxisevolution on 2009-01-23
Oh, and you may have to put the sudo command before your commands when accessing any devices after /dev/

So...

sudo hdparm /dev/hda


:popcorn:

---

### Post by yeats on 2009-01-23
What are you trying to do with dvd decrypter?  I'm sure there are alternative ways to do this with Ubuntu programs . . .

---

### Post by cowboy7305 on 2009-01-23
Trying to pirate dvds 
if there is a programe out there  ok 
I have tried using dvd rip and could not get that to work

---

### Post by oldos2er on 2009-01-23
> **cowboy7305 said:**
> Trying to pirate dvds 


 Then you probably won't get much help here.

---

