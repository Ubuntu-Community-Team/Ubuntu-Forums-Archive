---
title: "LiveCD Boot hangs at boot options"
date: 2010-04-22
forum: New to Ubuntu
---

### Post by DaveNorthCreek on 2010-04-22
Trying to install 9.10 from ISO I burned today, onto whitebox PC with VIA mainboard and Celeron CPU, along with various other bits and pieces.  I had a workable Ubuntu install earlier, and managed to kill it using apt-get dist-upgrade.
So I obviously shouldn't be trusted with sudo. :-)

To the issue:
No matter the boot options I enter in the Install Ubuntu screen (after hitting F6), I get a dialog box saying:
(Title) Boot Loader
/casper/vmlinuz
[OK]

occasionally, after the CD/ROM huffs and puffs, it says
(Title) Boot Loader
/casper/initrd.lz
[OK]

In any case, the CD/ROM whirrs merrily for a few minutes, and nothing else happens.

Any ideas how to force this process along, even just to the next step?

Thanks!
Dave Block
North Creek Consulting
Trying to add a server so my MacBookPro doesn't lock up all the time

---

### Post by tom.swartz07 on 2010-04-22
> **DaveNorthCreek said:**
> Trying to install 9.10 from ISO I burned today, onto whitebox PC with VIA mainboard and Celeron CPU, along with various other bits and pieces.  I had a workable Ubuntu install earlier, and managed to kill it using apt-get dist-upgrade.
So I obviously shouldn't be trusted with sudo. :-)

To the issue:
No matter the boot options I enter in the Install Ubuntu screen (after hitting F6), I get a dialog box saying:
(Title) Boot Loader
/casper/vmlinuz
[OK]

occasionally, after the CD/ROM huffs and puffs, it says
(Title) Boot Loader
/casper/initrd.lz
[OK]

In any case, the CD/ROM whirrs merrily for a few minutes, and nothing else happens.

Any ideas how to force this process along, even just to the next step?

Thanks!
Dave Block
North Creek Consulting
Trying to add a server so my MacBookPro doesn't lock up all the time

Hi Dave.

It sounds like you might have gotten a bad write on your installation CD. If you have another blank cd lying around, try re-writing the .iso file to the cd. Dont forget, you need to set it to a low speed to make sure that it is written with no errors.

Once you get it re-done, try booting again and then select "Check Disk for errors". This will assure that you have the proper image written to your cd. 


After that, you should be all set to roll!

---

