---
title: "[SOLVED] this laptop has an ATI Radeon Xpress 200M. Where's the drivers?"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by surelock22 on 2008-12-13
When my brother helped me install Ubuntu on my desktop, he helped me get the Nvidia driver for it. I'm guessing I'd get it through synaptic, but which one do I need?

Thanks!

---

### Post by theolster on 2008-12-13
[From the Community Documentation]("https://help.ubuntu.com/community/BinaryDriverHowto"):> If you have an ATI Radeon 9500 or newer (including thx X-series, such as x300, x1600, etc, an Xpress 200, or a Radeon HD card), then you can use the restricted fglrx drivers: [BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI").

Assuming that you are using the lastes Ubuntu Ibex, then this guide doesn't have instructions for you, but I'm guessing that trying the Hardy instructions would probably work...?  Let us know how you get on.

---

### Post by epitaph on 2008-12-13
I'm not sure why you would get/want the Nvidia driver for your ATi chipset. Ubuntu should have offered to allow you to enable some restricted drivers for your video card (which could be fglrx). At least that is the simplest way I can think of. I believe the package name is xorg-driver-fglrx.

---

### Post by surelock22 on 2008-12-13
Actually, I went through the Synaptic Package thingamajigger and typed in "ATI Radeon Express 200M" and a list of packages appeared, and I found out that I had already installed the driver, but it wasn't working correctly, so I re-installed it, rebooted, and when I check out the hardware drivers, it informed me that the ATI driver was up and running. In Accesories there was an ATI config program which gave me the specifics about which card i had and how the power was being used, so after seeing and using that I kinda came to the conclusion that my ATI card was working fine and dandy.

Hooray for Synaptic!!! +1 for Ubuntu!!! If the shoe was on the other foot and I was dealing with installing drivers for Windows, I know from experience that sometimes it can take longer than an hour figuring out how to get a driver to work correctly (SOMETIMES, NOT ALL THE TIME, JUST DEPENDS ON THE DEVICE AND THE DRIVER). I swear, everything I've had to get a driver for with the PC's I've installed Ubuntu on has been pretty easy to do, and pretty quick too. The ONLY thing I'd have to complain about is having to get the proprietary codecs running to do things like play DVD's, burn audio CD's (redbook) from MP3, reading MP3's, etc. etc., something that if I wasn't as computer literate as I am (and I'm not a true computer nerd by true nerd standards)I may have problems doing and finding the solution, something that Windows users don't have to go through, but with the proper training, (and the proper code and links) we can all overcome quite proficiently.

Believe me, I spread the word of Ubuntu as much as possible, because there are litterally millions upon millions of Windows users who don't even realize they have a choice, a better (and cheaper) choice.

:guitar:

---

### Post by surelock22 on 2008-12-13
> **epitaph said:**
> I'm not sure why you would get/want the Nvidia driver for your ATi chipset. Ubuntu should have offered to allow you to enable some restricted drivers for your video card (which could be fglrx). At least that is the simplest way I can think of. I believe the package name is xorg-driver-fglrx.


I'm sorry, but the desktop computer had an Nvidia card, the laptop has an ATI. Maybe my english is bad....

---

### Post by epitaph on 2008-12-13
You can make sure it's running well by running "fglrxinfo" in terminal. I'd test it by running "glxgears" too.

Glad to hear it's working well.

---

