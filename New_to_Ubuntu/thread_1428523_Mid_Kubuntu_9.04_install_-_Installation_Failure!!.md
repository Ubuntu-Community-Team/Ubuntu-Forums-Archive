---
title: "Mid Kubuntu 9.04 install - Installation Failure?!!??"
date: 2010-03-12
forum: New to Ubuntu
---

### Post by amh091 on 2010-03-12
I recently purchased an acer aspire one netbook equipped with windows xp... so naturally i decided to take kubuntu for a spin... i downloaded unetbootin and made myself a kubuntu 9.04 live usb stick. everything was working fine, until it got to a point during the installation where an error message appeared :

Installation Failure

The installer encountered an error copying files to the hard disk:

[Errno 5] Input/output error

This is often due to a faulty CD/DVD disk or drive, or a faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed, to clean the CD/DVD drive lens (cleaning kits are often available from electronics suppliers), to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment.


so now im kind of stuck in limbo... the installation process deleted the other OS on the petition, and now i cant fully install kubuntu. im currently running off of the live usb... 
any suggestions????

---

### Post by sandyd on 2010-03-12
redownload and burn the Kubuntu ISO onto a disc or usb drive.

make sure you check the md5sum of the ISO

---

### Post by Jazzy_Jeff on 2010-03-12
You could have a bad download of the image. Download it again and retry it. If for some reason it still does not work download the alternate install cd. It is text based but I have never had any problems using it.

---

### Post by TriBlox6432 on 2010-03-13
Isn't KDE a bit heavy for a netbook?

---

### Post by baddnady23 on 2010-03-13
When you burn it, burn at the slowest speed available to minimize the chance of errors during the burn process.

---

### Post by dlradlt on 2010-03-13
you'll have to use a different machine with a internet connection to rebuild your live usb

when you rebuild your live usb make sure you make a small persistant changes file so you can save your changes to it for while your working on your netbook 

gparted can be loaded into the live usb if you boot to the live usb with a live internet connection gparted is an excelent graphical partition manager and it will be able to see if your windows partition is still there as well as format resize and move partition's

I would manually partition your hard drive with gparted and use the advanced partitioning option durring the install to select your partitions if your trying to dual boot with windows. the default partitioning options have issues if your first install crashed after the linux partitions were created 

grub will find your windows partition and make it selectable durring the linux install if its still there....

also my wife has a emachine netbook with the same hardware specs as your aspire one and the regular kubuntu 9.10 install worked perfectly for me from a live usb

hope that helps.

L8r

---

### Post by amh091 on 2010-03-14
thanks drladit, that worked perfectly... much appreciated.

---

