---
title: "onboard graphics - install problems"
date: 2010-09-09
forum: New to Ubuntu
---

### Post by aussie.ian on 2010-09-09
I am wanting to install ubuntu 9.10 (live cd) to a pentium 4 machine with SIS onboard graphics. The problem is the only resolution i can use via the display manager is 800x600 4-3. Is there a way to manually select what resolution my monitor is run at.
Are these chipsets even supported any more as I've experienced this problem with other variants of linux also.

---

### Post by Naitsirhc Hsem on 2010-09-09
I would search sis and your graphics card model in the search box, I have had success with 11 year old graphics cards.  I think it is possible.  you should also look into xorg.conf resolution

---

### Post by aussie.ian on 2010-09-09
> **Naitsirhc Hsem said:**
> I would search sis and your graphics card model in the search box, I have had success with 11 year old graphics cards.  I think it is possible.  you should also look into xorg.conf resolution
I can't seem to find xorg.conf. Go to /etc/X11/ but no xorg.conf
Sorry i don't know what you mean by searching for my graphics card. Where would I do the search, how do I find out what model it is (it's onboard graphics)

---

### Post by Jazzy_Jeff on 2010-09-09
Unfortunately SIS is probably the worst video card ever made. I have never had good luck with them in Linux or Windows for that matter. I hope someone can help you here.

---

### Post by aussie.ian on 2010-09-10
Ok.. I have completed the upgrade to latest release now when I start my computer i get a message about running on low resolution then when I click ok to proceed the system starts and I get a message box which contains.
> FAILED TO LOAD /usr/lib/xorg/modules/drivers/sismediadrv.so
FAILED TO LOAD module "sismedia" (loader failed)
 NO DRIVERS AVAILABLE
According to winxp device manager the offending item is; 
SiS 661FX/GX Mirage Graphics

Any help with this will be greatly appreciated

---

### Post by Naitsirhc Hsem on 2010-09-13
[http://ubuntuforums.org/showthread.php?t=347451](http://ubuntuforums.org/showthread.php?t=347451)

---

### Post by Naitsirhc Hsem on 2010-09-13
[http://www.winischhofer.net/linuxsisvga.shtml](http://www.winischhofer.net/linuxsisvga.shtml)

---

