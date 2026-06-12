---
title: "No such file or Directory...Help"
date: 2010-02-23
forum: New to Ubuntu
---

### Post by sadimus on 2010-02-23
Ok here's my problem. I'm trying to install windows 7 unto my netbook. The problem is I've hit a roadblock, I'm using an intel mac to prepare my flash drive so it can be bootable. I unmounted it using diskutil unmountDisk /dev/disk2
Unmount of all volumes on disk2 was successful 

Which you can see was succesful. Now im trying to mount the windows7.iso image unto the flash drive and i keep getting this error. The image is on my desktop. Am I not specifying the path properly?

sudo dd if=/home/sadiq/windows7222.iso of=/dev/disk2 bs=1m
dd: /home/sadiq/windows7222.iso: No such file or directory



Can someone point me in the right direction please???

---

### Post by ikt on 2010-02-23
> **sadimus said:**
> The image is on my **desktop**. Am I not specifying the path properly?

> dd: /home/sadiq/windows7222.iso

shouldn't it be /home/sadiq/Desktop/windows7222.iso

?

---

### Post by theDaveTheRave on 2010-02-23
sadimus.

First off this is a linux forum? maybe you would be better off to contact the windows forums for installing windows 7 ! ;)

It also sounds like you are attempting to perform a "net install", so maybe you should search for this.

To be able to do so you need to have an ethernet card that is capable of a PBXE (pre-boot exection environment), so as you are able to hook into your desktop over your local network, it may be easier than using an ISO on a thumbdrive.

Also if you have another operating system on you netook and are attempting to install windows onto the same netbook you will run into problems. Windows doesn't like to be the second OS on any system, so you'll need to perform a "clean" install and this will involve formating any other OS that resides on the system - In other words, if you have any personal data on there, back it up first.

I would be unsurprised if trying to do a net-install where the windows image lives on a 'linux/unix server' isn't something that hasn't been performed before. So I'm sure that there would be someone out there who would be able to assist you in your venture... A quick look back at my (now rather old) XP MCSE/MCSA book (yeah I know it's horrid isn't it!), it suggests for a net install you will need to have some method whereby you can boot your target system where it will be 'network aware'.

Then on your desktop you will need the instalation files that are held within one of the subdirectories of the windows 7 ISO. This is the file that you need to point to (so it may well be similar on windows 7).

Here is a link to some instruction in doing a [network install]("http://blog.ryantadams.com/2008/02/01/how-to-boot-from-the-network-pxe-boot-with-tftp-and-windows-pe/"). Another thing to remember is to use the correct 32 or 64 bit process.

Good luck and report back here on your progress for other net admins who may find themselves doing the same thing in the future (I'm thinking I may have to do this also at some point! - sad isn't it :( ).

David

---

### Post by d3v1150m471c on 2010-02-23
Personally, I wouldn't use windows. I have xp for software testing but it's on virtualbox because it avoids the hazards that come along with grub and partitions. If you're trying to install to dual boot you'll need to section off a partition and then boot from the windows 7 cd or usb that you put the .iso on. Here's hoping it doesn't wipe ubuntu off your system anyways.

---

