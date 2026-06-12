---
title: "Screen Resolution in Kubuntu10.10"
date: 2011-05-29
forum: New to Ubuntu
---

### Post by ItBala on 2011-05-29
Can someone please help me in saving the screen resolution in my machine .. because whenever i'm starting the system, the screen uses the default resolution 1024*768...and i have change it every time back to 1280*1024 via Display and monitor settings...I'm facing this issue only in Kubuntu were as in ubuntu i was able to save the screen resolution settings ..

---

### Post by GWBouge on 2011-05-29
I doubt I can help, but for the sake of someone that might, could you give a little more information?  What type of graphics card/controller do you have?  Which drivers are you using?  Have you tried changing the resolution with the ATI/nVidia/whatever utility, or just through the OS's default tool?  Are you saving the changes to the xorg.conf file?

---

### Post by ItBala on 2011-05-29
Thanks for your help on this ...I'm using nVidia graphics card..and currently i'm just using OS default tool to adjust the screen resolution..

Please help me in using the nvidia utility and saving the configuration settings in the xorg.conf file..

---

### Post by GWBouge on 2011-05-29
Sorry it took me so long, been out the house all day.

I'm not too familiar with Kubuntu, but here's what I do on Ubuntu ...

Have you installed the drivers for the card?  With the proprietary drivers (look in 'Additional Drivers'), you'll get a utility called Nvidia-Settings.  Use the 'X Server Display Configuration' in there to adjust the screen resolution.  Then click 'Apply', make sure it works for you, and click 'Save to X Configuration File'.

Again, I'm not 100% sure exactly what everything is called in Kubuntu, or where they hide in the menu's, but that's pretty much it.

---

