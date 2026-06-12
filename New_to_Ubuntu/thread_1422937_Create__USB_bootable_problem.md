---
title: "Create  USB bootable problem"
date: 2010-03-06
forum: New to Ubuntu
---

### Post by navaneethan on 2010-03-06
In my laptop DVD drive not working properly,i mean can't able to install ubuntu hardy :-) so i wanna to install ubuntu 9.10 from usb
so i have planned to take the image to usb via **usb starter disk**option i chose make a start up disk bit it shows input/output error less no of files only copied to usb,

note: i used the distro ubuntu 9.10 to make usb startup disk

---

### Post by ubhi on 2010-03-06
> **navaneethan said:**
> In my laptop DVD drive not working properly,i mean can't able to install ubuntu hardy :-) so i wanna to install ubuntu 9.10 from usb
so i have planned to take the image to usb via **usb starter disk**option i chose make a start up disk bit it shows input/output error less no of files only copied to usb,

note: i used the distro ubuntu 9.10 to make usb startup disk


Download Unetbootin from  sourceforege & follow the instruction's


[http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/](http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/)

---

### Post by C.S.Cameron on 2010-03-06
Does your laptop have an OS on it now? 
How big is your thumbdrive?
Have you tried formatting your thumbdrive FAT32 using gparted?
At what point do you get input/output error?
Have you selected the thubdrive as first HDD in bios?

---

### Post by navaneethan on 2010-03-07
> **C.S.Cameron said:**
> Does your laptop have an OS on it now? 
How big is your thumbdrive?
Have you tried formatting your thumbdrive FAT32 using gparted?
At what point do you get input/output error?
Have you selected the thubdrive as first HDD in bios?

I am having latest ubuntu,2 gb size my thumbdrive,formatted the option shown there...i did it...copied some of the files after gave the option "start a new disk",but it shows input/output error unable to create a startup disk..

---

### Post by C.S.Cameron on 2010-03-07
Sometimes it is hard getting usb-creator to work, often,(as ubhi suggests), UNetbootin will do the trick.

---

### Post by navaneethan on 2010-03-08
then is any way to install uubntu hardy to my netbook without using cd-rom???

---

### Post by C.S.Cameron on 2010-03-08
Ah yes, I recall that 8.04 was before the time of usb-creator and had persistence broken, but it is LTS. I had problems using later versions of usb-creator to make start-up usb drives of Hardy.
Do you have the Hardy iso downloaded on your laptop? You can use UNetbootin to to mahe a start up thumbdrive or you can use the Hard Disk, Drive C:\ option of UNetbootin to make like a virtual "Live CD" on your hard drive so that the next time you boot you have the option to install Ubuntu from that virtual "Live CD".

UNetbootin is about 4.2 MB.

---

### Post by k3lt01 on 2010-03-08
Check out [this thread]("http://ubuntuforums.org/showthread.php?t=1288604"). I know it works as I have set up a flash drive and a usb external hdd.

---

### Post by C.S.Cameron on 2010-03-09
I understand "BootMyISO" automates the process in the above thread. It is only 246 KB but I have not tried it with Hardy.

---

### Post by Goveynetcom on 2010-03-09
I haven't dealt with Hardy myself, I joined around 9.04. But if your drive is broken and the usb method won't work, I recommend using a USB disc drive (if you have one). Might be inconvenient if you don't have one, but I had a similair problem installing WinXP on a laptop and had to use one.

---

### Post by Nicolas.Perrault on 2010-03-09
Try Pendrivelinux:

[http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/](http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/)

---

