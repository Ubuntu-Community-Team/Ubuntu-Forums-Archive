---
title: "ATI drivers"
date: 2010-10-06
forum: New to Ubuntu
---

### Post by daveboy23 on 2010-10-06
hi, this is one of the last things i need to complete my ubuntu exp.
i've been trying to install the ATI radeon HD 5470 on my computer using the ubuntu proprietary drivers.  after the install it asks to reboot after which booting just gives me a blank screen.  i get into ubuntu editing the boot (hope that what it's called - pressing x in grub) and entering "nomodeset" before splashscreen.
after that i just get in, disable the driver and continue without.

does anyone know how to install it?
thx

---

### Post by mörgæs on 2010-10-09
I assume that you are using 10.04.

The short answer is: ATI has not been very helpful supplying drivers for these cards, so if you have a screen picture it means that you are using open-source drivers. They are fine, but maybe a little slow if you are into gaming. 

One can not install closed-source drivers for these cards under 10.04. If it is a problem, I suggest you wait a few weeks and try 10.10 (not tomorrow, though it is the official release).

---

### Post by daveboy23 on 2010-10-09
why not tomorrow?

---

### Post by azertyh on 2010-10-09
> **daveboy23 said:**
> why not tomorrow?

because everyone wants to download the new release causing a traffic jam. wait few days or weeks.

---

### Post by mvklingeren on 2010-10-09
AMD ATI / fglrx is still a PITA when it comes down to Linux support

it annoyed me so much, i simply ripped out the AMD-ATI 4850 out of my rig, to use the onboard NVIDIA GPU 8200GS i got.

If you have other options then AMD ATI, use them.


Will never buy AMD ATI again.

---

### Post by carlgm on 2010-10-10
> **mvklingeren said:**
> AMD ATI / fglrx is still a PITA when it comes down to Linux support

it annoyed me so much, i simply ripped out the AMD-ATI 4850 out of my rig, to use the onboard NVIDIA GPU 8200GS i got.

If you have other options then AMD ATI, use them.


Will never buy AMD ATI again.

That's stupid, AMD drivers will get better and they have got decent open source drivers which in the future should be also suitable.

---

### Post by WRDN on 2010-10-10
The ATI drivers do work, but as mentioned previously, they can be a nightmare to install.
After a recent kernel update that I did (yesterday), FGLRX broke so I decided to install the latest ATI drivers.

I chose to install over the old drivers, rather than removing them first. This worked, but X.Org then threw errors if I tried to use any applications that used the GPUs capabilities (mostly OpenGL apps).

In the end I had to purge all applications related to ATI drivers (including many parts of the xserver), reboot, and install the new ATI drivers from, what was essentially, a clean graphics install.

---

### Post by daveboy23 on 2010-10-10
could you give me the ways to do it?
speak in noob language please

---

