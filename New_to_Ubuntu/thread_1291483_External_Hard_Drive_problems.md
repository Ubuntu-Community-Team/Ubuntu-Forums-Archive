---
title: "External Hard Drive problems"
date: 2009-10-14
forum: New to Ubuntu
---

### Post by antoinettey on 2009-10-14
I just bought a 500GB seagate external hard drive, when I plugged it in the first time it worked automatically and just let me drag and drop into the drive, however I tried to use the external hard drive to make a ubuntu startup for my friends pc through the usb startup disk creator in the admin, when my hard drive came up in the usb part, it said that i needed to format it before i could make the startup disk, well that i did, and now my hard drive doesnt show up on my laptop anymore? can someone please help me I really dont know what ta do or what im doing with it

---

### Post by LewRockwell on 2009-10-14
> **antoinettey said:**
> I just bought a 500GB seagate external hard drive, when I plugged it in the first time it worked automatically and just let me drag and drop into the drive, however I tried to use the external hard drive to make a ubuntu startup for my friends pc through the usb startup disk creator in the admin, when my hard drive came up in the usb part, it said that i needed to format it before i could make the startup disk, well that i did, and now my hard drive doesnt show up on my laptop anymore? can someone please help me I really dont know what ta do or what im doing with it

yes, this is the same experience that you would/will have with creating a bootable USB device

as long as it remains a bootable piece of media you'll have this issue

you can use fdisk, cfdisk, or a gui partition editor(gparted) to make changes to your media

if you don't know what these are...or require guides/tutorials...those can easily be located on the interwebs

you may select the one(s) you feel most comfortable with and proceed from there

.

---

### Post by LewRockwell on 2009-10-14
we also wanted to point out that it is best to properly partition these large external drives and use them for back-ups, clones, and medium-term storage

use more permanent media(CD/DVD) for long-term storage requirements

and use flash media(thumb drives, flash cards, etc) for easily bootable/changeable short-term applications

.

---

### Post by Paqman on 2009-10-14
The USB Startup Disk Creator is intended to turn a USB stick into a bootable live version of Ubuntu, like the LiveCD.

If you want to make a copy of Ubuntu that your friend can boot into, you should instead install Ubuntu (and the GRUB bootloader) onto your external drive. It will run pretty slowly though, so you might want to mention to your friend that installing to an internal drive will be a lot snappier.

---

### Post by Deadmode on 2009-10-14
Just so we can help you see what is going on please type ```
cat /etc/fstab
``` in a terminal and paste us your output for /etc/fstab file.

---

