---
title: "Why does my computer reboot itself?"
date: 2010-11-22
forum: New to Ubuntu
---

### Post by jocika011 on 2010-11-22
I have problem with Ubuntu 10.10 64-bit on my Intel Core I7 930 computer with 6GB RAM. Problem with reboot occurs whenever I am trying to copy/manipulate large files or sets of files (especially when I am using USB Stick).

I have dual boot (2 separate hard disks) Windows 7 and Ubuntu 10.10. 

**This problem does not appear on Windows 7.**

I have found the following solution that did not help:

[I]To solve that edit the file /etc/default/grub.
Find the line:

GRUB_CMDLINE_LINUX_DEFAULT=&#8221;quiet splash&#8221;

and change it to:

GRUB_CMDLINE_LINUX_DEFAULT=&#8221;quiet splash nomodeset&#8221;[/I]

Does anybody have any idea about solution?

[B]INTEL Quad Core I7-930 2.8GHz 
DDR3 6GB [3x2GB] DDR1333 (PC3-10666) 
GIGABYTE GA-X58A-UD3R ( Intel X58/ICH10R - Socket 1366 - QPI 6400 MT/s ) 
ASUS EAH5670/DI/1GD5 PCIe ( Radeon HD5670 1024MB DVI HDMI )
SATA300 1.0To (1000GB) - 7200 WESTERN Caviar Black[/B]

---

### Post by eriktheblu on 2010-11-22
Not sure why you would change Grub for this, but did you run
```
sudo update-grub
```after making the change?

Is it a complete shutdown and restart, or is more like you lost power? 

If you're chugging along on second and in your BIOS the next, I'd guess it's more of a hardware issue (power supply or overheating).

---

### Post by jocika011 on 2010-11-22
> **eriktheblu said:**
> Not sure why you would change Grub for this, but did you run
```
sudo update-grub
```after making the change?

Is it a complete shutdown and restart, or is more like you lost power? 

If you're chugging along on second and in your BIOS the next, I'd guess it's more of a hardware issue (power supply or overheating).

Sorry, I forgot to mention that i did "sudo update-grub".
It is more like computer loses power. Everything on the screen just disappear. After that, computer reboots.

Maybe hard disk with ubuntu making problem (regarding that another with Windows is OK) ...

---

### Post by eriktheblu on 2010-11-24
Boot loader is not the first thing I think of from what you describe. 

I still say overheating or power loss. It's possible that Ubuntu uses more of the hardware's potential than windows, thereby increasing power consumption and heat.

I would suggest: 
Opening the case 
Give it a good air dusting 
Sniff around for anything that smells burnt
Check your cables for loose connections, and stray wires that might be close to heat sources
Ensure there is proper airflow through the case and around components (hard drive too)
Install a temperature and voltage monitor (software) and ensure these stay within normal ranges. If they don't, adjust BIOS settings and/or check for a BIOS update.

During the reboot, the machine may communicate a code in the form of beeps. Your motherboard manufacturer should publish a guide to these codes.

If these fail to solve it, see if you can figure out how to throttle back the system resource usage. Not a real solution, but useful for diagnosis. I have not idea how that might be accomplished.

---

### Post by pricetech on 2010-11-24
My first thought is heat.  My second thought is PSU.  My third would be memory.

Advice above is good.  I'd probably put an extra fan somewhere to improve airflow and, if the system is located where you can, leave the case open and put a box fan blowing into it.

PSU is pretty much a "test by substitution" component.

Memory tests can be done using memtest.

Good luck with it.

---

### Post by pricetech on 2010-11-24
.

---

### Post by pricetech on 2010-11-24
.

---

