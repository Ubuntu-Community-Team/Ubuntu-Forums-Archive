---
title: "Need ideas how to boot USB external drive that is not recognized by BIOS"
date: 2010-09-19
forum: New to Ubuntu
---

### Post by sarc on 2010-09-19
Hi there,

I did a fresh install of Ubuntu 10.4 on a USB drive (including GRUB).  All my Notebooks rcognize and boot from this drive except for my newest, an HP probook 6555b.  This new HP Bios is a nightmare full of garb... ehm features for security, drive lock, fast booting Win7 and what not.  Anyway I tried all possible permutations of BIOS settings but it still refuses to show USB as a bootable option in multiboot.  

It does boot from CDROM so I'd like to know if anyone knows a workaround where I could have GRUB in CDROM leading me to boot from USB hard drive.  

p.s. Installing GRUB in the internal hard drive is not an option.. I don't want to touch it, it's my work notebook.

Thanks!!:guitar:

---

### Post by georgemc on 2010-09-19
Maybe this will work for you.

PLOP Boot loader - see the link

[http://www.plop.at/en/bootmanager.html](http://www.plop.at/en/bootmanager.html)

I know it works for me on an old ASUS a2500, the only way I can boot from a USB drive on that laptop.  Download it and burn to a CD/DVD.  Then boot from the CD and select from the menu your USB device.

Hope this helps.

George

---

### Post by irunwithscissors on 2010-09-19
> **georgemc said:**
> Maybe this will work for you.

PLOP Boot loader - see the link

[http://www.plop.at/en/bootmanager.html](http://www.plop.at/en/bootmanager.html)



I'll second George's recommendation. I'm using PLoP as a boot manger on a USB stick just so I don't have to mess with the MBR on the windows drive... works like a champ..

---

### Post by sarc on 2010-09-20
It worked perfectly!  Thanks guys!

---

### Post by supergeek67 on 2010-11-27
Other than bootmanagers, restart your laptop and press F2 to show start up options (or F10 to show Bios if that didn't work) and change the boot order:  1)CD/DVD DRIVE 2)USB STORAGE  3) INTERNAL HDD etc.  than it should boot from usb hdd or flashdrive.

---

