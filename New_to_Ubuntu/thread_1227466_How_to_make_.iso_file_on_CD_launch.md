---
title: "How to make .iso file on CD launch"
date: 2009-07-30
forum: New to Ubuntu
---

### Post by Johnecash on 2009-07-30
Hi 
 
I have downloaded 
 
xubuntu-8.04.1-alternate-i386.iso
 
onto my computer and burned it onto a CD using 
 
ISORecorderV2RC1.msi
 
as per the beginners handbook
 
does anyone know now how to make the CD launch the xubuntu installation program
 
(there is nothing called setup.exe on the disk iso file)
 
thanks

---

### Post by daimaru on 2009-07-30
uhm you just pop it in your cd drive reboot your computer and if you do not have your cd drive as the first boot device you enter the bios boot menu (normally thats F2 or ESC F12 etc depends on your computer, but it says so at startup. just watch the bottom of your screen where it says "hit del to enter setup" or hit F2 to enter multiboot ... ) 

then the xubuntu installer launches and you can select install.

---

### Post by philcamlin on 2009-07-30
> **daimaru said:**
> uhm you just pop it in your cd drive reboot your computer and if you do not have your cd drive as the first boot device you enter the bios boot menu (normally thats F2 or ESC F12 etc depends on your computer, but it says so at startup. just watch the bottom of your screen where it says "hit del to enter setup" or hit F2 to enter multiboot ... ) 

then the xubuntu installer launches and you can select install.

+1 :popcorn:

---

### Post by mikewhatever on 2009-07-30
You have to reboot the computer with the CD in the cd-rom, and if the BIOS is set to boot from cdrom, the cd will get autolaunched. Backup your files before installing.

---

### Post by Johnecash on 2009-07-30
ok I am in the BIOS menus now
 
it says 
 
boot device priority
A:
C:
PXE
 
does anyone know how to put the cd drive at the top of the list?

---

### Post by Johnecash on 2009-07-30
or even get the cd drive (its drive d:) on the list at all in the first place?

---

### Post by daimaru on 2009-07-30
> **Johnecash said:**
> ok I am in the BIOS menus now
 
it says 
 
boot device priority
A:
C:
PXE
 
does anyone know how to put the cd drive at the top of the list?
never mind the bios menu. you can change the boot priority there if you want. normally you do that using + and - sign, but every computer has a "enter bios setup" and "enter boot menu" option at startup. instead of hitting "del" key you have to hit the other key it says to hit. ..sorry I cant be more specific, but on my laptop it is F12 on my Desktop its F2 on your computer it might be F-Whaterver, just read the text at bottom of screen and hit "ctrl+alt+del" if you missed it , so you dont have to start windows or ubuntu everytime ; )

---

### Post by Johnecash on 2009-07-30
ok will try that when I get home. thanks for your help guys.

---

### Post by Johnecash on 2009-07-31
HI none of this worked
 
none of the other F keys work at boot time
 
the only F key that works at boot time is F2  which takes me into the Bios menus which doesnt have the launch from CD option. 
 
Any help?

---

### Post by mikewhatever on 2009-07-31
You must be able to boot from something to launch the installer, be it cdrom or usb. If the BIOS doesn't support either of these options, perhaps a BIOS upgrade is in order.

---

### Post by Johnecash on 2009-07-31
does anyone know how to do a bios upgrade

---

### Post by jacklinux on 2009-07-31
it should say your driver (CD driver) name and then use the '+' key as needed to move UP

---

### Post by louieb on 2009-07-31
How old is this PC? Can you post the make and model? Better yet CPU type and amount of ram. Does it have a floppy drive? 

Sounds like its old and doesn't support booting from a CD. There is a work around - you can make a boot floppy.  [SmartBootManager - Community Ubuntu Documentation]("https://help.ubuntu.com/community/SmartBootManager") boot with the floppy and the floppy will boot the CD.

> does anyone know how to do a bios upgrade

BIOS is custom made for each type and model motherboard. Only way I have done it is to open the case - find the the motherboard part #. and Google bios upgrade for <motherboard part #>.  May or may not find one.

---

### Post by Johnecash on 2009-08-02
- it is very old - 1998 
 
its a dell p3 500mhz with only 128m ram and 7gb hdd
 
Do you guys think I should bother and or should I just buy a newer $500 box for Linux project?
 
Will a computer this old be alble to recognise my wireless network? Ubuntu on my new laptop did it fine. 
 
 
Thanks for the help - I'll try and make a boot floppy

---

### Post by louieb on 2009-08-02
Those old Dells max out at 256 mb ram. Thats the main drawback. Interesting to play with but going to be slow with Xubuntu, even for surfing the net and email. A light distro such as Puppy or PCLinuxOS will perform ok.  

They do have PCI slots 2 or 3 so a wireless card should work.  Try making a SBM floppy as see if you can get it to boot to a CD that way. 

You should be able to get a decent used computer. Look for a P4 2gHz with 512mb ram - 1 GB would be better. If you have Craigs List for your area look there. I've see them in the 100-200 dollar range.

Good Luck.

---

### Post by Johnecash on 2009-08-03
hey - thanks for the advice - I bit the bullat and bought a new (old) pc at my local computer market for AUD300 _ Compac Presario dual core 1 gb ram 200gb hdd
 
I installed ubuntu 9.04 and the thing is flying - its great - now I just have to learn about my new OS - thanks for all your help guys.
 
I should have done this 3 days ago rather than fiddling around with a p3 Junkyard dog

---

