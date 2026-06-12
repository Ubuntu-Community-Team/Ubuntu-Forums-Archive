---
title: "Can't get past login screen 10.04"
date: 2010-11-28
forum: New to Ubuntu
---

### Post by TheTeamFromMars on 2010-11-28
Hi, 

I can't get past the ubuntu 10.04 login screen this morning for some reason...
After I enter my password - nothing happens. 

I've been using ubuntu 10.04 for a few months and it has been working fine until now.
 
I didn't change/install/uninstall anything yesterday so I don't know what's wrong. 

Does anyone know how to fix this please???

Thanks.

---

### Post by warfacegod on 2010-11-28
If you have an older kernel in your GRUB menu, try one of those.

---

### Post by jw12321 on 2010-11-28
Another possibility is that you could be low on disk space.

---

### Post by warfacegod on 2010-11-28
A good thought. Booting into a LiveCD would be a good way to find out and clean up if needed.

---

### Post by Rubi1200 on 2010-11-28
What graphics card do you have installed?

---

### Post by TheTeamFromMars on 2010-11-29
Hi guys, 

Thanks for your help. I tried logging in today again and it worked fine...

Not sure what the problem was but I have 60GB of disk space left so I don't think it was that. 

Rubi1200 - Sorry, I have no idea what kind of graphics card this thing has... :o| I know how to switch it on but that's about it I'm afraid :o)

Thanks again for your help!!

---

### Post by Rubi1200 on 2010-11-29
You are more than welcome :)

If you run into problems again, be sure to ask here first ;)

In Ubuntu, to find out what graphics card you have go to Applications > Accessories > Terminal and copy/paste the following:
```
lspci | grep VGA
```
The output will provide you with the relevant information.

---

### Post by TheTeamFromMars on 2010-11-30
Thank you!

Graphics card is Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

Thanks for the advice...

---

