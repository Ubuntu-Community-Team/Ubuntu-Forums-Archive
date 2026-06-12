---
title: "stuck on screen after loading ubuntu after having boot"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by kevin Luhver on 2008-12-15
i have a acer AM5200 E5521A 4GB ram AMD 64, quad core processor ati readon HD 3650, 

and i downloaded the 32 bit cd of Ubuntu, and i reboot me Pc i get the screen where ubuntu asks me for the language, than i get the menu where it says try ubuntu without any changes to your computer, install ubuntu, check CD for defects, test memorie and some other last thing, anyways i have chosen so many times install Ubuntu, with the diff. altreantives (F4) and i also tryed the F5 options and F6 as well and still each time i try to install Ubuntu i get passed the loading of Ubuntu with the orange bar but right before the end, the colour goes negative for a milisecond and my screen goes black with a blinking underscore ( _ ) than after like a min or two i get a screen where it first says loading, please wait...
than it has info on ubuntu, i guess to keep you busy while it loads, it has writen on the screen, ubuntu is a no waranty sofware totaly free, ect ect. and i always freeze or get stuck on that screen and ubuntu wont go further. yesterday i had that screen on for almost 7 hours and still nothing, 


please help?

---

### Post by Tatty on 2008-12-15
At the first boot screen (where it says install without making changes etc...) press F6.  This will let you edit the boot command.  Delete the words "quiet splash" off the end, then press enter.

This will boot without the splash screen and with verbose output, see if it gives any errors when it hangs.

---

