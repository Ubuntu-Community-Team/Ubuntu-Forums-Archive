---
title: "Flashy Blue Pixels Problem"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by Kiddalee on 2008-12-07
Hiya.  I've begun to run Ubuntu 8.10 on an Acer Aspire 5004WLMi.  I've left visual effects off since the beginning.

Now there are places on the display that are supposed to be dark coloured, but instead flash blue.  It only happens to very dark colours, and then only where there is shading in the image involved.

I've tried changing the screen res from 1280:800 to 1280:768 and that only made it worse.  Oh, and now I'm unable to change back to 1280:800.

This is when the problem began: I was going about my business, plugged my computer in just in time for the battery to run out, had to turn the poor thing back on, and have since had this problem.

---

### Post by James Keating on 2009-05-13
You have  Silicon Integrated Systems display. The driver is on your system but not active. 

As root, edit the file  /etc/modules
from the command line:
sudo gedit /etc/modules

add the line
sisfb

which is the module for the proper driver

save and reboot

---

