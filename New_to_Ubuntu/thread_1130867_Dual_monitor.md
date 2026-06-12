---
title: "Dual monitor"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by Chapeen on 2009-04-20
Hi guys,
I got a dual monitor at home but the weird thing is that I made it work just by using gnome's display manager.I don't even have my ATI graphics card driver installed.

I Installed the ATI driver and Ati catalys control panel, but then I just had mirror screens, so I unistalled the driver.

I'm not sure if I should keep it this way or try to fix it with the ATI driver.

One last thing, when I had the Ati catalys control panel there was some menu that were greyed out, and a popup said that I need administrative rights, how can I enable those menus. (One of those menus was Xinemara which I believe is use to correct the mirror situation.)

what a long text lol !! soorry

---

### Post by Anthon on 2009-04-20
The ATI catalyst control panel probably should be configured to ask you for sudo priviliges. What I would try (there might be better ways). I to check wich application gets started (using ps -eax) and then close the app and start that it from the commandline with an explicit sudo in front of it.
HTH

---

### Post by Chapeen on 2009-04-20
I ran the ATI catalyst Control Panel with sudo, I still don't have the options to enable xinemarra beacause it says that I only have 1 monitor enable and that I should enable it by going to Display manager.When I launch the Display Manager it freezes !

Is there another way to enable xinemara?

---

