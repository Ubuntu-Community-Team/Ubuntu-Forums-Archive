---
title: "Moving HDD to a new Motherboard"
date: 2009-08-19
forum: New to Ubuntu
---

### Post by Ducatiboy Stu on 2009-08-19
My motherboard died and I am about to move my HDD to another one which will be totally different with respect to CPU

I have XP and 9.04 with grub setup on the drive and want to know if they ( or even just Ubuntu ) will boot up and what issues I am going to have

---

### Post by owise1 on 2009-08-19
I do not think that this will worry the ubuntu install.  Would not be too confident with the XP installation.  I think that I read a comment in the Linux Format magazine a couple of months ago where they did just that - the linux bit just worked but the XP bit went into enless reboots.

Cheers

---

### Post by oldfred on 2009-08-20
I did this just a few months ago. Ubuntu worked just fine. Windows had problems as it was trying to boot but would not boot until it got a permission slip from Bill G. saying it was ok. Finally after a few reboots Windows was ok'd, and it worked. 
The only other minor issue was when I first plugged in the drives ( I had 3 drives) they were in a different order do the wrong MBR was seen, but I was able to adjust the order in BIOS.

---

### Post by kellemes on 2009-08-20
> **Ducatiboy Stu said:**
> My motherboard died and I am about to move my HDD to another one which will be totally different with respect to CPU

I have XP and 9.04 with grub setup on the drive and want to know if they ( or even just Ubuntu ) will boot up and what issues I am going to have

Depends on how Ubuntu and XP are able to handle the new hardware.
Last week I upgraded Motherboard/Proc/Memory (to 64 bit) and Ubuntu-32 threw me a lot of kernel-panics and other scary messages (eventhough it should work afaik). An install of Ubuntu-64 solved all issues.

Anyway, never assume it will work, create backups of all your data.

---

### Post by alexlafreniere on 2009-08-20
Ubuntu will not have a problem with the new MB, just disable any extra drivers you might have installed and it'll boot up just fine. XP will throw temper tantrums, so you'll probably have to reinstall. At least I had to last time I did this.

---

### Post by wizard10000 on 2009-08-20
Ubuntu shouldn't complain much - with XP install all the hardware drivers for the new box before you move it to the new machine.

---

### Post by Bartender on 2009-08-20
I'm not as confident as above posters.  I've tried the same thing with an Ubuntu HDD.  It's worked about half the time.

I guarantee you that Windows will not cooperate.  Microsoft may have left many problems unaddressed but they've been all over making sure you don't get to slip a new MB under an old installation.

---

### Post by gradinaruvasile on 2009-08-20
It worked for me. Changed an ASUS M2V-TVM (VIA chipset) to ASUS M3N78-VM (Nvidia chipset). I had on the M2V-TVM a Nvidia Geforce GS7600 vid card with the latest (185.18.31) drivers installed from nvidias site. On the new one i left the onboard Nvidia 8200 to see how it works.
Switched the MB in the case, put the HDD in, powered on, and everything was working out of the box (sound, network ,compiz and stuff).
Your mileage may vary. Just make sure u buy hardware supported by ubuntu.

---

### Post by oldrocker99 on 2009-08-20
I simply quit using XP last year in utter frustration and installed Hardy.

Last summer, a lightning strike took out the network chip on my motherboard, rendering it unbootable. I bought a new motherboard, with a completely different chipset, and I had to reboot Hardy twice to get it up. That was all.

Another reason to turn my back on M$.

:guitar:

---

### Post by LewRockwell on 2009-08-20
+1

wow, if ever there was a great time to use clonezilla to back everything up and then do fresh installs...now is the time!

or...

you could even get another hard drive, partition it to your pleasure, and then do the fresh installs on it

after that's done then you can mount your old hard drive as a slave or external and gather anything of value off of it

+1

Wheeeeeeee, this computin' stuff is fun!

.

---

