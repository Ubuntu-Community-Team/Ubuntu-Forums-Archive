---
title: "error 22"
date: 2009-06-29
forum: New to Ubuntu
---

### Post by tobiasolesen on 2009-06-29
Hi 

I had NBR installed in a dual boot with windows on an eee pc. I want to install eeeNBR so i deleted the regular NBR. 

The problem is that when I boot my computer I get the error 22 and can not enter windows (which I need to do before installing eee). It is not the boot.ini which have changed... I looked at it through the live cd which I am using now...

I can not boot windows and have error 22 when booting

I need to get rid of Ubuntu as a first...

thanks 
tobias

---

### Post by halitech on 2009-06-29
here is info on fixing grub

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

on second thought, if you have the windows install cd, boot it, go to recovery and fix the mbr

---

### Post by tobiasolesen on 2009-06-29
hi 

- as i run

sudo grub

- and then

find /boot/grub/stage1

- i get error 15: file not found..



I tried doing

sudo mkdir /mnt/root

but also get an error, it says cannot create since file exists... 

I am not familiar with the terminal...

I do not have the windows cd


thanks for the effort

tobias

---

### Post by halitech on 2009-06-29
wait, you already deleted the partition where grub was installed (along with NBR)?

if so, you will need either a. the windows install cd (which you say you don't have) or b. supergrub so you can repair the mbr,

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

