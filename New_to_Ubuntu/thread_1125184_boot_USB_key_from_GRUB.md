---
title: "boot USB key from GRUB"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by dimdom on 2009-04-14
Hi there, 

I'm wondering if there's a way to configure grub to look at a USB key
for the kernel to boot (LIVE USB - Ubuntu 8.10)? 
The BIOS doesn't allow it as an option under the boot sequence settings, and I can't find any other settings there pertaining to USB. 
Would I have to rebuild grub to add the USB drivers? 
What device would I tell grub to look at?


Thanks,
dimdom

---

### Post by brujoand on 2009-04-14
im not sure.. but if your usb key will be recognised as /dev/sdb and its / partition would be /dev/sdb1 you could try to add /dev/sdb1 partition to you menu.lst and you should atleast get the choice to boot from it.. 
worth a try!

anders

---

### Post by Jakey_TheSnake on 2009-04-14
Are you talking about booting from a LiveUSB? Or just pointing your currently installed Ubuntu to look for its kernel on the USB? 

To boot from the LiveUSB, enter your BIOS settings (should be something like F1, F10, F12 or DEL - it will tell you on-screen somewhere before you reach GRUB) then move the "USB HDD" option to the top.

---

### Post by tea for one on 2009-04-14
Just a few questions before I can try and help you:-

(a) Do you have Grub installed on your HDD (i.e. in an existing Linux OS)?

(b) Are you trying to boot a "live" USB system without having a BIOS option to boot from USB?

The instructions for (a) are different to (b).

(a) In essence, you can install (i.e. not "live") Ubuntu to a USB stick and copy the menu.lst entry to Grub on the HDD. You have to be aware of the Grub convention for drive identification i.e HD0, HD1 etc.

(b) You can run a "live" USB but install Grub on a bootable CD
Have a quick look at this tutorial [http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-810/](http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-810/)

---

