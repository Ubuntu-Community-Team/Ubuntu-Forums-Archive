---
title: "Screen Freezing Revisited"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by daniell59 on 2009-11-25
In my previous thread I lamented how my screen would freeze and the mouse would not function. Re-booting did no good. But shutting off the power then powering back on solves the problem.
They say instead of cursing the darkness, light a candle.

Someone please explain to me what is going on.

Please!

---

### Post by mikewhatever on 2009-11-25
Well, rebooting probably resets the system, so that whatever errors there were are not after startup.;)

---

### Post by daniell59 on 2009-11-25
> **mikewhatever said:**
> Well, rebooting probably resets the system, so that whatever errors there were are not after startup.;)

Thanks, where do I go from  here?

---

### Post by pi.boy.travis on 2009-11-25
If you could please provide some information about your hardware.  Graphics card, RAM, motherboard, etc.  Thanks.

---

### Post by daniell59 on 2009-11-25
> **pi.boy.travis said:**
> If you could please provide some information about your hardware.  Graphics card, RAM, motherboard, etc.  Thanks.

CORSAIR XMS2 DHX 4GB (2 x 2GB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400) Dual Channel Kit Desktop Memory Model TWIN2X4096-6400C4DHX - Retail

  ASUS EAH3450/DI/256M Radeon HD 3450 256MB 64-bit GDDR2 PCI Express 2.0 x16 HDCP Ready Low Profile Ready Video Card - Retail 

 ASUS P5Q Pro LGA 775 Intel P45 ATX Intel Motherboard - Retail 

 Intel Core 2 Duo E8400 Wolfdale 3.0GHz 6MB L2 Cache LGA 775 65W Dual-Core Processor - Retail

---

### Post by pi.boy.travis on 2009-11-25
> **daniell59 said:**
> CORSAIR XMS2 DHX 4GB (2 x 2GB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400) Dual Channel Kit Desktop Memory Model TWIN2X4096-6400C4DHX - Retail

  ASUS EAH3450/DI/256M Radeon HD 3450 256MB 64-bit GDDR2 PCI Express 2.0 x16 HDCP Ready Low Profile Ready Video Card - Retail 

 ASUS P5Q Pro LGA 775 Intel P45 ATX Intel Motherboard - Retail 

 Intel Core 2 Duo E8400 Wolfdale 3.0GHz 6MB L2 Cache LGA 775 65W Dual-Core Processor - Retail


If you have not done so already, go to System>Administration>Hardware Drivers , and check for a proprietary driver for your graphics card, that may mitigate the issue. . .

---

### Post by daniell59 on 2009-11-25
> **pi.boy.travis said:**
> If you have not done so already, go to System>Administration>Hardware Drivers , and check for a proprietary driver for your graphics card, that may mitigate the issue. . .

Thanks

I have done as you instructed. So far I have had two successful reboots without having to cut power. I will keep you posted.
I see that much of the trouble that I am having is caused by my lack of knowledge. I do not have a basic understanding of Ubuntu.

---

### Post by daniell59 on 2009-11-29
It happened again. The mouse froze when re-booted. Only by powering down was I able to activate the mouse. I would appreciate insight.

Thanks

---

### Post by pi.boy.travis on 2009-11-29
Your freeze is either caused by a hardware or software failure, and now we will divide the problem space be determining which is failing. . . 

When you power on your computer, are all the fans spinning?  You may want to open your case to confirm.  Are your CPU and GPU running at their normal operating temperature?  The ASUS or ATI website may provide a utility to confirm this, or you could search the repositories.  I know that Nvidia has a Linux version of their driver control software, but I am not sure about ATI or ASUS.  Is your power supply running at the proper voltage?  If you have the means, can you run Windows or another Linux distro without it freezing?

Are there any conditions present at every freeze?  Is it always at boot/login?  When the computer is frozen, wait and see if the clock on the panel in the upper-right-hand-corner updates.  When the computer is frozen, can you use Ctrl+Alt+F1 to switch to a text console?

Linux in general rarely freezes, and when it does, it is usually due to a hardware failure, or a driver issue.  There is a lot of technical info up there, so just take it slow and steady, and ask any and all questions you have.  

Hope this helps. . .

---

### Post by nhbob on 2009-12-18
I also am experiencing this. I have searched and it seems to be a common problem. Why it is not being addressed by the Ubuntu developers is a mystery. It appears it MAY be a problem with the video card/chip.  I have tried to remove compz as recommended resulting in corrupted files which required a complets reload of Ubuntu.  Result? The new installation also randomly freezes. Takes three or four attempts to get to an active screen.

---

### Post by pi.boy.travis on 2009-12-19
We still need more information about the nature of the freeze to help. . .

---

### Post by nhbob on 2009-12-19
Letme try:

I am running Ubuntu within Windows XP as a sperate partition. I
am using an ASUS NFORCE 2 A7N8X DELUXE-LAmotherboard with an AMD XP 2500 with 512 of DNR memory and an ATI RADEON 9000 (128) viseo card. No propriatary drivers show up under Ubuntu.

When I log an I successfully enter my password and go to a brown screen with panels outlined andsometimes with some icons and others not.  The mouse works but left "clicks" have no affect so the screen is effectively "frozen".  Right click will show avaailable instructions.

This does not occur every time I attempt to log on but quite often - 50% or more. Restart usually finanlly gets me to a new screen but sometimes wafter 3 or 4 tries.  At times I have had to completely shut down one or more times.

I did some research and have tried just about everything but I am a biginner so I may not have performed actions properly.

It was suggested I shut off graphic affects.  I did thsi with no success.  I then tried to remove compiz from the system.  This was no easy task. I  dicsvored I had corrupt files of some kind. I tries to use windows to delete fiels but with little success. Finally during a Start under Windows the system "discovered the corrupt files and rebuilt the system.

Let me mention one other thing I ran into while attepting the above. Advise was to enter Ubuntu in recovery mode to enter commands.  WHENI DID THIS I COULD NOT GET BACK TO THE GUI AFTER ENTERING"exit". Any ideas on this.

This along with having a very difficult time converting from OUTLOOK MAIL to Thunderbird under ubuntu is making me question why I am going through this to begin with.!:rolleyes:

---

