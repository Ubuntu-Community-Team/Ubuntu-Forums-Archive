---
title: "cd-rom problem"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by samsung72 on 2008-12-05
Ubuntu 8.04  AMD Athlon 800MHz  HDD 20GB  Ram 512 Mb

Hi there, this is my first post. I am having problems with my Samsung SM-304B CD-Rom, it can read cd's and cd-r's with no problems but when I try to read cd-rw's or dvd's the drive locks and I can not remove the disk until I reboot. I have had this problem with ubuntu 7.04, 7.10, and 8.04. I know that the drive is ok because the disks I use to install Ubuntu and run live disks are cd-rw. I have read other posts with similar problems and they have asked for printouts from: sudo lshw -C disk, which is as follows:

 *-cdrom
       description: DVD reader
       product: COMBO SM-304B
       vendor: SAMSUNG
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: BS02
       serial: 2SAMSUNG COMBO SM-304B   BS020
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 status=ready
I hope that someone can help with this problem.
Thanks in advance from samsung72

---

### Post by samsung72 on 2008-12-07
Perhaps I should have mentioned that this is a dual boot system with Windows XP and Ubuntu 8.04. The cd-rom drive works ok with Windows XP with cd/r, cd/rw, and dvd disks. So this is an Ubuntu issue which has persisted in Ubuntu 7.04, 7.10 and 8.04. 

If no solution can be found is it possible to eject the cd from the terminal to save having to reboot?
samsung72

---

### Post by residualbit on 2008-12-07
to unmount from the terminal you can run:```
sudo umount /dev/cdrom/
```

not sure about the other issue as I rarely use cd-rw.

---

### Post by samsung72 on 2008-12-07
nkirk1 thank you for replying. I tried what you suggested

code:
desktop:~$ sudo umount /dev/cdrom/
[sudo] password for : 
umount: /dev/cdrom/: Not a directory

then I tried it without final forward slash

desktop:~$ umount /dev/cdrom
umount: /dev/scd0 is not mounted (according to mtab)

but the cd-rom drive is clearly mounted as the cd is shown on the desktop and the music is only paused. I was using a cd-r just to try it out

I don't have much experience using the terminal and bash
samsung72

---

### Post by mc4man on 2008-12-07
How about just using ```
eject
```

---

### Post by samsung72 on 2008-12-08
mc4man, I tried using "eject" from the terminal, and it did eject a cd-r disk, but it will not eject a cd-rw disk (the disk is still stuck in there now :-) ) I even tried sudo eject but to no avail. If I go to the cd-rom icon in computer and select "eject" I get a warning message saying "Unable to mount media-There is probably no media in the drive". I get the same message if I select "mount". Under the cd-rom icon it says "CD-RW/Blu-ray-RE Drive" which is clearly wrong as Blu-ray was never heard when this computer was made. I wonder if the correct driver is installed? Thank you for trying.
samsung72

---

### Post by mc4man on 2008-12-08
Considering the length of this problem a solution may not be forthcoming.
It seems the drive isn't reading/mounting disks with file systems, though this is only an assumption that the cdr's you can use are 'audio' cd's.

Is this a sata or ide drive?

---

### Post by sneeks on 2008-12-08
can you not try a different cd drive,may be a hardware problem.

---

### Post by samsung72 on 2008-12-09
Hi sneeks, if this cd-rom drive didn't work 100% in Windows XP on all disks, I would have tried a new drive long ago. I have had this problem with Feisty, Gutsy and Hardy and is the only real problem I am having with Ubuntu. I have tried an external usb dvd-rom drive from another computer and everything works ok with that with the same disks but that's not really solving the problem. Thank you for your interest
samsung72

---

