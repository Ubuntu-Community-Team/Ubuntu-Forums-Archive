---
title: "Help needed on deleting partition in windows and then installing ubuntu"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by michael berg on 2009-03-07
Hi All,

My Hard disk is 160GB divided into four logical drives C,D,E,F of each 38 GB.I am planning to delete partition F by using Disk Management option in windows so that it will create 38GB of unpartitioned space.What should i do while installing ubuntu to use this unpartitioned space.

P.S.: I did not take back up of C,D,E drives.Is it compulsory to do so?

Regards
Michael

---

### Post by Dadsgé on 2009-03-07
if you want to be sure you don't do anything wrong, i recommend to take a backup.

for the installation: know how big the partitions are before you start the live-cd
then in terminal: sudo fdisk -l
this should give you a list of all partitions of your harddrive, and also external drives like usb
here you search the name of the partition you want to use for ubuntu
it should be something like sda1 of sda2, if you just look at how big the partitions are, you should be able to see which one is the F partition in windows.
if you now the name, just install ubuntu, when you come to the point of partitioning, do it manually and chose the partition with the name you just searched.
click on the partition, then use partition, as EXT2, and mountpoint / (if you want a separated /home partition, you just need to decrease the amount of MB of this partition and use the extra partition as /home, this can be useful if you reinstall ubuntu, then you just don't format this partition and you will keep all your preferences, like icons, desktopbackground,...) don't forget to install a swap area if you are planning to use the suspend and hibernate option, i didn't do it, because i didn't need it. 
i think this will be it
good luck and have a good time using ubuntu ;)

---

### Post by Dadsgé on 2009-03-07
ow, forgot something, 
if you want your pc to boot in windows, you've got to change the menu.lst file in grub.
if you set it to boot automatically in windows and you want to use ubuntu, just press ESC when you get a black screen saying 'grub loading'

to open the menu.lst file:
```
sudo gedit /boot/grub/menu.lst
```

just above timeout.sec you see 'default', there you've got to change the number
but first you've got to know which number is windows
scroll down in the file till you see
"## ## End Default Options ##"

there you find a list of all installed kernels, first the ones of ubuntu, then windows
just count the amount of 'titles' (the first one is 0!)

this can give some problems when you update your system.
sometimes there is an ubuntu-kernel 'extra' installed
just recount and change the number again ;)

for example i've got 5 titles, the first one is 0, the last one is windows, then i should insert the number 4 to make it boot automatically in windows

---

### Post by michael berg on 2009-03-12
Hi,

Can i use knoppix Live CD to resize the existing windows partition to create unpartitioned space because i cannot take backup of my data.

Regards
Michael

---

### Post by antoz on 2009-03-12
You can use the partition editor of the Ubuntu live cd as well to do your partitions. 
To answer your question in the first post it is not compulsary to back up but but always highly recommended.
Just make sure that your windows partitions are [COLOR="Red"]NOT CHECKED[/COLOR] for formatting and you should be OK 
Good luck, A.

---

