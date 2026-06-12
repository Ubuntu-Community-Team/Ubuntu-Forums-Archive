---
title: "How to install from USB"
date: 2009-07-11
forum: New to Ubuntu
---

### Post by Poincare101 on 2009-07-11
I already have ubuntu but I'm reinstalling it. I went into system -> administration and made a USB boot up disk. But, even when I have changed the boot selection of my computer to keep "Removable Devices" in first priority, it doesn't recognize the USB drive and goes directly to GRUB. What should I do?

---

### Post by earthpigg on 2009-07-11
have you tried plugging it into different USB ports?

your bios _*may*_ only support booting from one of them... or, if it is an older computer, may not support booting from USB at all. :\

---

### Post by Poincare101 on 2009-07-11
Its a fairly new computer. We bought it in late 2006.

---

### Post by earthpigg on 2009-07-11
> **Poincare101 said:**
> Its a fairly new computer. We bought it in late 2006.

should be ok then... i'd try different USB ports, and double check the BIOS to ensure that boot from USB is set to highest priority.

---

### Post by LewRockwell on 2009-07-11
> **earthpigg said:**
> should be ok then... i'd try different USB ports, and double check the BIOS to ensure that boot from USB is set to highest priority.

and/or you can do it manually at start-up by depressing "F12" approximately twice per second until the boot device selection menu comes up

if it doesn't work from there then I would say your thumb drive didn't get set-up correctly to be seen as a bootable drive

.

---

### Post by Poincare101 on 2009-07-11
I did do the F12 thing and skips right ahead to the hard drive once the LED on my flash drives blinks for a bit. I haven't tried different ports yet.

---

### Post by Poincare101 on 2009-07-11
I have tried all the USB ports and none of them seem to work.

---

### Post by LewRockwell on 2009-07-11
> **Poincare101 said:**
> I did do the F12 thing and skips right ahead to the hard drive once the LED on my flash drives blinks for a bit. I haven't tried different ports yet.

indicates thumb drive is not bootable to me

back to the tech table

.

---

### Post by earthpigg on 2009-07-11
> **LewRockwell said:**
> indicates _*thumb drive is not bootable*_ to me

i wasn't aware there was such a thing as a non-bootable thumb drive...

---

### Post by sneeks on 2009-07-11
you make the drive bootable using gparted,set the flag to boot,and this may cure your problem..

---

### Post by LewRockwell on 2009-07-11
> **earthpigg said:**
> i wasn't aware there was such a thing as a non-bootable thumb drive...

if a piece of media, optical or otherwise, is not set-up to be bootable then the BIOS will move on to the next device in line

this is why an ISO must be burnt properly and not just copied/duplicated

same for a hard drive...if no partition is marked with a boot flag then the drive will be passed by as "non-bootable" and considered "static data"

.

---

### Post by bigken on 2009-07-11
do you have support for legacy usb in your bios ?

---

### Post by Crafty Kisses on 2009-07-11
If you have a working Ubuntu installation, try plugging the USB drive in one of the USB ports and run:
```
lsusb
```
See if the drive is recognized.

---

### Post by LewRockwell on 2009-07-11
> **Codename said:**
> If you have a working Ubuntu installation, try plugging the USB drive in one of the USB ports and run:
```
lsusb
```
See if the drive is recognized.

"oh, that's so page-oneish"

.

---

### Post by earthpigg on 2009-07-11
> **LewRockwell said:**
> if a piece of media, optical or otherwise, is not set-up to be bootable then the BIOS will move on to the next device in line

this is why an ISO must be burnt properly and not just copied/duplicated

same for a hard drive...if no partition is marked with a boot flag then the drive will be passed by as "non-bootable" and considered "static data"

.

o, right... i thought you where saying hte thumb drive itself was physically incapable of being set up to boot from. :lolflag:

---

