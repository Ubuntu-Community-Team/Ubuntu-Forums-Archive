---
title: "Entering a disk using the bootable cd and unlocking files"
date: 2009-12-07
forum: New to Ubuntu
---

### Post by Mgpgebert on 2009-12-07
I have an error 18 and the only way i can access my hard disk is through the bootable cd.How can i unlock my files using my password before i save them.

---

### Post by mbzn on 2009-12-07
from the live cd you can just use the sudo command (no password needed).

---

### Post by lisati on 2009-12-07
> **Mgpgebert said:**
> I have an error 18 and the only way i can access my hard disk is through the bootable cd.How can i unlock my files using my password before i save them.
> 
**Forum Feedback & Help**
Report technical problems with the website here (i.e. broken features), or ask questions pertaining to forum features.
   ...

---

### Post by Mgpgebert on 2009-12-07
I really need more help for using the sudo command.Thnks

---

### Post by Sin@Sin-Sacrifice on 2009-12-07
You ```
sudo mount /dev/yourdrive /where/you/want/to/mount
cd /where/you/mounted
``` Then you have access to your files.

---

### Post by Mgpgebert on 2009-12-07
ubuntu@ubuntu:~$  sudo mount /dev/media/home/aurore/images/photos
mount: can't find /dev/media/home/aurore/images/photos in /etc/fstab or /etc/mtab
 This is what i get!! All i want is to get the access to those files so that i may copy them. Other wise can i repair this error 18 ?

---

### Post by JamesParnell on 2009-12-07
wouldnt it be /dev/sda1(or whatever partition it is)..... 
 
i am a total noob to this stuff, so its probably wrong...

---

### Post by JamesParnell on 2009-12-07
_[COLOR=#0000ff][http://lmgtfy.com/?q=How+to+fix+grub+error+18](http://lmgtfy.com/?q=How+to+fix+grub+error+18)[/COLOR]_
_[COLOR=#0000ff][/COLOR]_ 
google is your friend

---

### Post by Mgpgebert on 2009-12-07
My hard disk is identified as 39.6 GB media

---

### Post by Sin@Sin-Sacrifice on 2009-12-09
Dude... come on. Your drive is actually hd0 which is aliased as an /dev/hda (ide drive) or /dev/sda (sata drive) and each partition will be /dev/sda#. This can be found using ```
fdisk -l
```. So... run fdisk and it will show you what each partition is named then you make a folder in /media or wherever you want to mount it. Such as /media/mydrive using ```
sudo mkdir /media/mydrive
```. Then you take the information that fdisk gave you to use ```
sudo mount /dev/sda1 /media/mydrive
```. Then you can open a folder in the drive and do as thou wilt.

---

