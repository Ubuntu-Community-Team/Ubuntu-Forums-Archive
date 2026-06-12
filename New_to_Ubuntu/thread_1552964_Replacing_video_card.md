---
title: "Replacing video card"
date: 2010-08-14
forum: New to Ubuntu
---

### Post by kbozz71 on 2010-08-14
Hey guys, if I replace my ATI video card with an nvidia one, will it screw up my installation? Or will it pick up the new hardware drivers and prompt me to install? Using mint 9. Thanks

---

### Post by NewDisciple on 2010-08-14
I believe that I had read somewhere (maybe this forum) that after changing to different hardware you had to reinstall.  Maybe someone out there knows differently? I do know that I did this the last time I swapped video cards.

---

### Post by NCLI on 2010-08-14
You shouldn't have to reinstall.

Before turning the computer off the switch the cards uninstall the closed driver for your ATi card using System->Administration->Hardware Drivers. This should ensure that there are no problems. 

After installing the new card, Ubuntu should automatically switch to using the basic open-source nVidia drivers. 
In order to utilize the full power of your new card, simply fire up Hardware Drivers again and install the closed driver.

---

### Post by vhoward1122 on 2010-08-21
> **NCLI said:**
> You shouldn't have to reinstall.

Before turning the computer off the switch the cards uninstall the closed driver for your ATi card using System->Administration->Hardware Drivers. This should ensure that there are no problems. 

After installing the new card, Ubuntu should automatically switch to using the basic open-source nVidia drivers. 
In order to utilize the full power of your new card, simply fire up Hardware Drivers again and install the closed driver.

Thanks for this. I just bought a new HP desktop and set up Ubuntu 10.04 in a dual boot. The on board ATI graphics chip in this computer is whimpy and can't perform for the compiz settings. I was hoping I wouldn't have to re-install when I install the new graphics card I want.

---

