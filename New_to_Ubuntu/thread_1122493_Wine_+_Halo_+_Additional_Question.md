---
title: "Wine + Halo + Additional Question"
date: 2009-04-11
forum: New to Ubuntu
---

### Post by Gp. on 2009-04-11
Hi,
I upgraded wine to the latest beta.

Weird thing is when I check out the "about" in the wine configuration, is says it's 1.1.18 not 1.1.19...
why is this?

Also when I try to install Halo using wine, the fonts are messed!

---

### Post by keplerspeed on 2009-04-11
Have you installed the required packages using winetricks? see here [http://appdb.winehq.org/appview.php?iVersionId=2720](http://appdb.winehq.org/appview.php?iVersionId=2720)
you require runtime environments, and also the fonts package, from winetricks.

As an alternative to winetricks, follow this tut, or just make sure you have the required dll's in system32 directory in your .wine c: drive.

---

### Post by Gp. on 2009-04-11
I've installed Mfc42.dll, and as far as I can see that's all that was required on that page.

What other packages are required with winetricks?

---

### Post by keplerspeed on 2009-04-11
For the fonts, try installing corefonts, see here [http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

About the wine version... possibly just a bug, the version details havnt been updated??? Who knows. If you compiled it from source, and your sure it was latest, I would worry.

---

### Post by Gp. on 2009-04-11
I can't install the core fonts. 

It gives me error status 127?

---

