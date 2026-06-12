---
title: "vista on one hdd then linux on other problem"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by 5dollafootlong on 2009-01-21
ok i Installed vista first on one hdd then ubuntu on my other hdd
now when i boot my pc I dont get a vista option in grub. but all the vista 
files are still there on the installed drive. is there a way to boot into vista or can i reinstall vista but will i then not be able to boot into ubuntu? im confused.

---

### Post by Crafty Kisses on 2009-01-21
You can try editing your GRUB config file and manually adding Windows Vista, see if that does anything, try the following:
```
sudo gedit /boot/grub/menu.lst
```
Once you're in your GRUB config, add the following lines at the bottom of the file:
```
title Windows Vista

root (hd0,0)

makeactive

chainloader +
```
Depending where Vista is located root (hd0,0) will vary just to let you know, so try that, and if that doesn't work, please post back and either I or someone else can help you further.

---

### Post by 5dollafootlong on 2009-01-21
ok thanks for your help 
now im getting a vista option but i get and error 
ERROR #1 must be absoute path or block list

i also see that ubuntu is on hd0,0 so what should i set the vista 
drive to in grub

---

### Post by Crafty Kisses on 2009-01-21
So try to set Vista as the following:
```
root (hd1,0)
```
I'd also like to see the results of this command:
```
sudo fdisk -l
```

---

### Post by 5dollafootlong on 2009-01-21
greg@dashiz:~$ sudo fdisk -l

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd485d485

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       35002   281153533+  83  Linux
/dev/sda2           35003       36481    11880067+   5  Extended
/dev/sda5           35003       36481    11880036   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x51a263a7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60802   488384512    7  HPFS/NTFS

---

### Post by 5dollafootlong on 2009-01-21
the 500gb is my vista drive as i said earlier my vista files are intact 
we just need grub pointed in the right direction. ty im such a noob

---

### Post by 5dollafootlong on 2009-01-21
ya no go with hd1.o

---

### Post by 5dollafootlong on 2009-01-21
if i cant get the windows path installed in grub could i drag my important
stuff to the linux drive being careful to not over write the linux partion?
then reinstall grub with the live cd ?

---

### Post by bumanie on 2009-01-22
Looks as though your drives have reversed themselves somehow. You can try either one of two things A) You could try altering the boot order in bios - as long as the /boot/grub/menu.lst is correct (ie has windows on (hd0,0)). or B) If windows is recorded as (hd1,0) in the grub menu.lst, between makeactive and chainloader add these lines

map (hd0) (hd1)
map (hd1) (hd0)

If you can boot into ubuntu, you can post the output of > cat /boot/grub/menu.lst and someone can help you further re whether to use A) of B). As you said, it looks as though vista is fully intact.

---

### Post by 5dollafootlong on 2009-01-22
ok ive sorted out the problem with your help thanks ubuntu community for the win :p

---

