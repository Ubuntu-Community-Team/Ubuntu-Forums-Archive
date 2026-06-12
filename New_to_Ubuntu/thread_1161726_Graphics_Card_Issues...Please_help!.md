---
title: "Graphics Card Issues...Please help!"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by khaos28 on 2009-05-17
OK, so i'm new to ubuntu and what not, and i've tied installing the driver to my graphics card (nVidia Corporation NV44A [GeForce 6200] (rev a1)) and i can't run it off of PCI from my bios. when i try running my graphics from my onboard, i have to start in low detail. it says my driver is activated. is my driver the wrong one? it;s like version 180 or something like that.

---

### Post by khaos28 on 2009-05-17
OK, so i'm new to ubuntu and what not, and i've tied installing the driver to my graphics card (nVidia Corporation NV44A [GeForce 6200] (rev a1)) and i can't run it off of PCI from my bios. when i try running my graphics from my onboard, i have to start in low detail. it says my driver is activated. is my driver the wrong one? it's like version 180 or something like that.

UBUNTU wont boot up with the bios set to PCI

---

### Post by overdrank on 2009-05-17
threads merged

---

### Post by khaos28 on 2009-05-17
Can i get step by step step by step instructions from anyone? preferable ones where i switch the control in the bios fro PCi to onboard and all that?

---

### Post by sideffects on 2009-05-17
Okay, let me explain his problem(I've been trying to help him with it.) His first issue was that the LiveCD wouldn't boot so he  demoted the Nvidia GeForce 6200 graphics card in his PCI slot and made his onboard graphics card default in the BIOS, and then Ubuntu LiveCD ran and installed just fine. Then he switched the graphics cards back so that the Nvidia was default in the BIOS and he said that the OS just froze on a black screen, but he was able to type (he said he got a TTY error). From that point on, the only way that Ubuntu would run is if he used the onboard graphics card, but it kept him in limited graphics mode. He said he tried to install the driver, but it still didn't work, so we downloaded Envy to install the driver with, and Ubuntu still wouldn't boot up.

Anyway, I hope that made sense. If someone has some thoughts or ideas it would be greatly appreciated. Thanks in advance!

---

### Post by diablo75 on 2009-05-17
Hmmm... Here's what I'd try:

If there are any other PCI cards in the PC besides the video card, remove them temporarily and try again.  This is just to rule out the rare possibility of some sort of hardware conflict.  At this point, I would also consider reseting the CMOS to factory defaults by using the clear jumper on the motherboard (or disconnect the power cord, remove the button battery from the motherboard and wait 5 minutes before putting it back).

If that doesn't help, verify the card actually works by putting it in a second known working PC to see if it will boot with any problems.

You mentioned it booting into low graphics mode... I'm assuming the nvidia drivers were manually installed when the card was not in use?  You should try to make sure your card and version 180 will play nice.  It might be recommended to actually use a slightly older version (the recommendation will be stated in your Hardware Drivers Manager if you ever manage to get Ubuntu to boot while the card is installed and set to be the PCs primary display adapter).

---

### Post by khaos28 on 2009-05-17
Well the only way i can get it to come up is in the low graphics version, with my onboard as my primary adapter. Currently there are no other PCI slots being used, and the Card was working just fine yesterday before i put Ubuntu on my computer. But when i try to get Ubuntu to load with my card set as the primary adapter, it goes to the load screen and stops maybe 10% of the way, it freezes here and just doesn't move past it. I have tried recovery mode as well, but the code that comes up on the black screen also freezes as well.

---

### Post by sideffects on 2009-05-17
> **khaos28 said:**
> Well the only way i can get it to come up is in the low graphics version, with my onboard as my primary adapter. Currently there are no other PCI slots being used, and the Card was working just fine yesterday before i put Ubuntu on my computer. But when i try to get Ubuntu to load with my card set as the primary adapter, it goes to the load screen and stops maybe 10% of the way, it freezes here and just doesn't move past it. I have tried recovery mode as well, but the code that comes up on the black screen also freezes as well.

Are you sure that you installed the driver for your Nvidia graphics card and not your onboard graphics card. Since the Nvidia one is not enabled you will have to install it manually, it shouldn't detect it automatically.

---

### Post by sideffects on 2009-05-17
Most recently, we've tried adding the BusID line to the xorg.conf file, but no dice. Any other suggestions?

---

