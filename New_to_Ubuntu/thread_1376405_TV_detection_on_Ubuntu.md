---
title: "TV detection on Ubuntu"
date: 2010-01-09
forum: New to Ubuntu
---

### Post by romaurie on 2010-01-09
I have a Sparkle Geforce 9500 GT graphics card onnected by S-VHS to S-VHS to my TV.It detects on Xp and Windows 7 but only when the OS starts.What do I need to install on Ubuntu to enable detection?
Romaurie

---

### Post by Darce on 2010-01-09
Hi romaurie,

I have a laptop with Nvidia 9500M GS. I run Ubuntu 9.10 and I have installed the v185 Nvidia drivers ( System->Administration->Hardware Drivers )

If your setup is the same, go to System->Administration->NVIDIA X Server Settings and the Settings Application will run.

Click on X 'Server Display Coniguration' and you should see all you displays if they are plugged in (Monitor,VGA-out,S-Video-out). If not, make sure all your displays are plugged in and press the 'Detect Displays' button and with any sort of luck it should appear.

Select the display you want to turn on from the 'Model' drop down box or by clicking on it in the layout window. Press the 'Configure' button and select 'Twinview'.

Now you can select resolutions and screen positions etc.

Hope this helps.

Cheers,

Tim

---

