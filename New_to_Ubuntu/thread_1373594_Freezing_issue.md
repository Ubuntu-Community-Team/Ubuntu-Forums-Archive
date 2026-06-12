---
title: "Freezing issue"
date: 2010-01-05
forum: New to Ubuntu
---

### Post by JR899 on 2010-01-05
Today is the first day im trying Ubuntu, install went smoothly and all that. When i booted back up and loaded Ubuntu up, it gets to the desktop and freezes within seconds, and does not unfreeze at all, which forces me to have to hit the switch on the surge protector and cutting power off to the computer. Any help, suggestions would be greatly appreciated with the issue. Thanks

---

### Post by SchizmWolf on 2010-01-06
What kind of computer are you running, and what version of ubuntu are you running? What are the specs on it (graphics card, RAM, etc)? That kind of information would be helpful. From what you've given, I would recommend booting with a LiveCD. If that works, try reinstalling Ubuntu. If not, burn another disk on a slower setting (i'd suggest 4x) and try again.

---

### Post by Zoot7 on 2010-01-06
Does this happen with any other OS's other than Ubuntu?
Normally lock ups that prevent you from doing anything are caused by faulty memory, I'd say to run a memtest just to be sure to sure if you haven't done so already.

---

### Post by JR899 on 2010-01-06
Its a HP Compaq, trying to run version 9.10, has Intel chipset, 1gig ram, 2.80 GHz Intel Pentium processor. The live CD freezes up as well, gonna try burning on a slower setting shortly. 
And no, it does not do it with any other OS, i am able to boot vista up fine, just not Ubuntu

---

### Post by Zoot7 on 2010-01-06
It might be a bad burn, have you tried the "Check Disk for Errors" option?

---

### Post by JR899 on 2010-01-15
sorry it took so long to respond, been busy, but i re burned the disc at a slower speed and checked that disc for errors before starting, said it was fine so i re installed. every was going good, things were working great till about 20 mins in it froze up once more.

---

### Post by warfacegod on 2010-01-15
This seems like a hardware issue. It could be bad Ram as zoot7 said, a failing hard drive, or an over heating processor are the most likely culprits. Although any bad hardware could potentially cause your system to freeze.

First I would clean the heat sink on the processor, replace the thermal grease if you take it off.

Run a memtest from GRUB, as zoot7 suggested, and replace if needed.

If you still get freezing, swap the drive out with a spare if you have one.

---

### Post by scorp123 on 2010-01-16
> **Zoot7 said:**
> It might be a bad burn  In that case the installation would have failed because in case of a bad burn because there would be corrupted archive files on the CD .... ;)

So if the installation succeeds without error messages about archive files that could not be read you can safely assume that the CD is OK ;)

---

### Post by kenuf on 2010-01-16
Noob here also....   but my friend had this problem when he hooked up to an old monitor...  He had to boot to safe graphics mode until he had done the Update manager Then he was able to operate without the freezes.

---

### Post by kansasnoob on 2010-01-16
I had the same problem with Karmic and troubleshooting it was such a pain I just decided to stick with Jaunty. Both Hardy and Jaunty are very stable on my hardware.

I tend to think it's an incompatibility issue with Karmic's Xorg. Anyway Hardy is supported for another 16 months and Jaunty for another 10 months, so I see no urgency.

---

### Post by scorp123 on 2010-01-16
> **kansasnoob said:**
>  I tend to think it's an incompatibility issue with Karmic's Xorg.  I've seen that too with Karmic, especially with low-end ATI cards ...

---

