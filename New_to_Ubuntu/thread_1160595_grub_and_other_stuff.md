---
title: "grub and other stuff"
date: 2009-05-15
forum: New to Ubuntu
---

### Post by pendulum101 on 2009-05-15
just installed windows 7 onto my laptop and was wondering how i would go about reinstalling the boot loader, also wondering if this can be done without reinstalling ubuntu as i have files i want to keep, if not thats ok cos i have them backed up.
thanks in advance

---

### Post by albinootje on 2009-05-15
> **pendulum101 said:**
> just installed windows 7 onto my laptop and was wondering how i would go about reinstalling the boot loader

See here : [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by albinootje on 2009-05-15
The easiest might be the -> Using the Unofficial "Super Grub Disk" section.
Although I personally found the SuperGrub menu choice a little bit confusing at first :)

---

### Post by sundar_ima on 2009-05-15
ya i also suggest you to have a look at Super Grub Disk. i have use it earlier and fout it simple...

---

### Post by pendulum101 on 2009-05-16
> **albinootje said:**
> See here : [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)y 

tried to reinstall grub using the method described and it worked to some extent, while it did give me access to my ubuntu partition i seem to have lost the ability to load windows 7 for some reason. also i get a warning message when booting up ubuntu saying something about ignoring some directory and owning a partition i can get what it actually says if its necessary

---

### Post by hobo14 on 2009-05-16
You need to keep following the guide through step #6, put:

 title Windows XP/Vista # You can use any title you wish, this will appear on your grub boot menu
 rootnoverify (hd0,0) #(hd0,0) will be most common, you may need to adjust accordingly
 makeactive
 chainloader +1

in /boot/grub/menu.lst  Change (hd0,0) to point to the (disk,partition) that windows is on.

I'd say yes, post your error message, no-one can help you unless you do.

---

### Post by presence1960 on 2009-05-16
> **pendulum101 said:**
> y 

tried to reinstall grub using the method described and it worked to some extent, while it did give me access to my ubuntu partition i seem to have lost the ability to load windows 7 for some reason. also i get a warning message when booting up ubuntu saying something about ignoring some directory and owning a partition i can get what it actually says if its necessary

run in terminal: ```
sudo fdisk -l
``` this will give you your partition info. You need this to add Windows to your menu.lst file. Post the output here and we'll give it a go.

---

### Post by pendulum101 on 2009-05-16
thanks for the advicer but i decided to take things into my own hands and i reinstalled everything from scratch. thanks everyone

---

