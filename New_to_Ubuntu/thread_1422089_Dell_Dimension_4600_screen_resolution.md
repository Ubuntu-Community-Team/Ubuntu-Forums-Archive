---
title: "Dell Dimension 4600 screen resolution"
date: 2010-03-05
forum: New to Ubuntu
---

### Post by japhyr on 2010-03-05
Hello,

I am trying to refurbish a dell dimension 4600.  I have installed 8.04.3, and it is fully updated.  The video card is an Nvidia NV18 GEForce4 MX 440 AGP 8x.

If I use the open source driver, the highest resolution is 800x600.

If I use the proprietary driver, the resolution goes to 640x480.  I can't use nvidia-settings, because the resolution is so low that I can't click on the resolution drop down box.  When I click on it, the screen jumps to a different place.

Is there a way to get a higher resolution out of this setup?  If not, the computer will go to the recycle pile.

Thanks.

-Eric

---

### Post by Tamlynmac on 2010-03-05
Have you tried downloading and installing EnvyNG from [here]("http://albertomilone.com/envyngfaq.html#A") then installing the driver? Just read and follow the instructions. I used to have the exact same card in 8.04 and installing EnvyNG worked.

Good Luck & hope this helps.

---

### Post by japhyr on 2010-03-05
I installed EnvyNG and tried to let it auto configure.  That led to a black screen.  I went to grub and fixed the x server, then tried the 3 manual choices for nvidia drivers in the Envy menu - 173.17.12, 96.43.05, and 71.86.04.  Each of these led to a black screen.  Am I doing anything wrong?  Is there anything else to try?

---

