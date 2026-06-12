---
title: "Possible to create a dual boot live USB"
date: 2009-10-06
forum: New to Ubuntu
---

### Post by ericeclifford on 2009-10-06
Well I was wondering if it is possible to make a dual boot live USB.

This would basically mean taking 2 live cd iso images, and making them onto the USB.

But I tried this, and I could not find a way to make it so I can switch between them.

Anyone know what type of customization I need to make this possible.

Remember the Live USB is not the installed version( it erases everything at a reboot)

---

### Post by Kreaper on 2009-10-06
i thought that the BIOS looks at the medium and loads the Bootloader so you might be able to try to make GRUB work on the Usb, but other than that just use a Usb and a CD, but these are just my thoughts so...

---

### Post by Sarmacid on 2009-10-06
I know for a fact that you can have many live distros in a usb drive using grub, and I know you can make at least one persistent, my guess is you can have more than one.

Just google around how to install grub2 on a usb.

---

### Post by executorvs on 2009-10-07
I was looking into this about two days ago and couldn't find an explanation of how other than doing a full usb install. 

I **assume** it would mean either reconfiguring syslinux or replace it with Grub.

if you find a an explanation please share.

---

### Post by executorvs on 2009-10-07
[http://www.dslreports.com/forum/r19335083-how-to-make-USB-stick-dual-boot](http://www.dslreports.com/forum/r19335083-how-to-make-USB-stick-dual-boot)
and
[http://www.dslreports.com/forum/r19335083-how-to-make-USB-stick-dual-boot](http://www.dslreports.com/forum/r19335083-how-to-make-USB-stick-dual-boot)
are the first things I've been able to find. I'm late for class so I'll look more later today.

---

### Post by C.S.Cameron on 2009-10-07
I understand that you can only have four bootable systems on a flash drive as this is the max number of partitions allowed, just like on a mechanical hard drive.
You can do a full install to the flash drive by clicking "install" after booting the Live CD, (ubiquity). This should automatically install grub to handle the other systems on the drive.
If you wish to dual boot with XP this page:
[http://www.ngine.de/article/id/8](http://www.ngine.de/article/id/8)
Tells how to install XP on a flash drive.

---

### Post by Sarmacid on 2009-10-07
I've tried the instructions here to install grub 2 on a USB and am able to boot a couple of live linux distros, haven't tried to make a persistent one though [http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)

---

