---
title: "having a hardtime with Riva TNT2 and Visual effects"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by xsabrewulf on 2009-05-21
I have 9.04

I have tried installing the Nvidia 71 drivers nothing shows up in hardware drivers

reinstalled 9.04 and tried using Envyng when I do it that way I get errors about unable to load nvidia_drv.so and it puts in me in a low graphics mode

after installing the drivers i did a gedit /etc/X11/xorg.conf and changed it to "nvidia"

so envy does not work

and when I install the 71 drivers normal nothing shows up in the hardware


i am a newb and I dont know what to do, i have googled the issue and still nothing.


any help would be great


also i checked the x log file and it says error loading nvidia module "nvidia"

---

### Post by overdrank on 2009-05-21
Hi and I believe the Riva TNT2 does not support the desktop effects. :(

---

### Post by xsabrewulf on 2009-05-21
Really because it support Open GL.

thought I read ppl have been running it


are there any steps I should do? because it never shows up in the hardware driver

---

### Post by xsabrewulf on 2009-05-21
anyone?

still stuck here :)

---

### Post by Steelmourne on 2009-05-21
You could try manually downloading the drivers from nvidia or going to System, Administration, Hardware drivers and checking the options there. Maybe its time to upgrade too. A 9500GT would run any effects for around $100.

---

### Post by xsabrewulf on 2009-05-21
this pc is not really worth upgrading but I do find the rotating cube handy... dont care too much about other effects...

if I add the drivers manually still nothing comes up in Hardware drivers

---

### Post by anewguy on 2009-05-21
I had a tnt2 card and it was missing support for somethings needed for desktop effects to run.  Running glxinfo in a command window showed some things missing.

Dave :)

---

