---
title: "failure to boot after ati install"
date: 2009-09-08
forum: New to Ubuntu
---

### Post by bernhardt00 on 2009-09-08
Hello all!  
I had created a usb stick of 9.04 (persistant) and saw that my ati card was not enabled.  when I activate the driver and try to reboot, I get a blank screen. It does not even want to display the start up screen.  I then reformatted the drive (fat32) and started again, able to function just fine until I get itchy and want to activate the driver.  I tried using the terminal to activate it, that gets me a garbled screen after attempting to boot

Kind Gentle people your wisdom is appreciated.

---

### Post by misfitpierce on 2009-09-08
This was the case for me on 9.04 only... I still use but am just using the ATI opensource driver that auto got installed. The fglrx driver did not auto update the xorg or something so it caused it to only display a blank black screen upon boot. I just erased my xorg and let it reboot to where I could see and made sure it was back to opensource driver. I will hope this is refixed by karmic koala release.

---

