---
title: "Is there a Linux boot disk  (floppy) wis USB driver?"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by TheIllustriousPotentate on 2009-05-03
Ok, I am trying to install Ubuntu on my Dell Inspiron 7000 laptop, but it will only load so far before stopping. I have determined that it is the CD rom drive of the laptop that just stops working partialy through the CD setup.

I have a stand alone CD rom drive that plugs in via USB, but the only problem is that the Dell Inspiron 7000's BIOS does not support booting from USB. I only have the option of booting from the hard disc, CD rom, or floppy disk. The floppy drive works fine, so I was wondering if there is a Linux boot disk that I can get that will load USB drivers so that I can boot up into some kind of RAM drive with USB support so that I can hook up the stand alone CD rom drive and start the installation of Ubuntu from the stand alone CD drive?

---

### Post by LowSky on 2009-05-03
[http://www.ehow.com/how_2138434_ubuntu-boot-disk.html](http://www.ehow.com/how_2138434_ubuntu-boot-disk.html)

---

### Post by Old_Grey_Wolf on 2009-05-03
Could use UNetbootin to make a bootable USB. [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by TheIllustriousPotentate on 2009-05-03
> **LowSky said:**
> [http://www.ehow.com/how_2138434_ubuntu-boot-disk.html](http://www.ehow.com/how_2138434_ubuntu-boot-disk.html)


Thanks for the link, but it seems the info on this page doesn't give the correct way to write the files to the floppy disk. it states that you have to type " ntrawrite -f sbm.bin -d a: " on the command line, but the computer insists that ntrawrite is not a valid command.

---

### Post by Old_Grey_Wolf on 2009-05-03
> **TheIllustriousPotentate said:**
> Thanks for the link, but it seems the info on this page doesn't give the correct way to write the files to the floppy disk. it states that you have to type " ntrawrite -f sbm.bin -d a: " on the command line, but the computer insists that ntrawrite is not a valid command.

Your BIOS gives you the option to boot from a USB stick. So the UNetbootin link I provided above may help you. Best wishes on your install.

---

