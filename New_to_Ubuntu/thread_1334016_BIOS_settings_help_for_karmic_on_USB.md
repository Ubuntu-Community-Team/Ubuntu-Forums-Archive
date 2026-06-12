---
title: "BIOS settings help for karmic on USB"
date: 2009-11-22
forum: New to Ubuntu
---

### Post by MisFitt on 2009-11-22
Hi,
I'm terribly confused.
I've created a Karmic USB on a 16GiB flash stick using the usb creator on Jaunty.
My bios offers as boot devices:
Floppy,LS120,Hard Disk,CDROM,ZIP,USB-FDD,USB-ZIP and USB-CDROM.
I've tried every usb setting available and the start-up doesn't provide any options other than "boot from CD",please help!
Thankyou:confused:

---

### Post by Sealbhach on 2009-11-22
Possibly, the USB you made did not work correctly and is not bootable. From that list you have, I would say the option you need is USB-FDD. Make sure you have them all in the right order too i.e. USB before Hard Drive.

.

---

### Post by 3rdalbum on 2009-11-22
Some computers can't boot up from USB Startup Disk Creator disks; try using Unetbootin to create the live USB.

---

### Post by MisFitt on 2009-11-22
Thanks,I'll try again.
I made the usb using the USB Startup Disk Creator in jaunty.
I put in the Karmic disk and requested and it seemed to go thru the process.
Is there something I should also do?

---

### Post by quinnten83 on 2009-11-22
try creating the USB startup disk from Karmic live cd.
You should format the disk to FAT32 first. that made the difference for me.

---

### Post by MisFitt on 2009-11-22
Thanks,i did do that and I've now tried 2 flash sticks in case there was some malfunction.
All the files are there,it's the bios I can't set to boot.
It would install if I allowed it so....???....bios,getting it to boot,bummer....

---

### Post by Sealbhach on 2009-11-22
In that case, your computer bios may not support boot from USB so the only other option would be try burning a CD image instead.

.

---

### Post by MisFitt on 2009-11-22
Thanks,yes i fear that is looking to be the case.
When I bought this computer I had no idea about USB bootables nor Ubuntu for that matter.
What a shame,though i haven't quite given up.I have all the paperwork and specs still so I'll try to find out for sure.
thanks very much for your time,I appreciate it.
I have the cd btw and my dvd/cd drive makes a lot of noise when spinning(needs replacing soon).

---

