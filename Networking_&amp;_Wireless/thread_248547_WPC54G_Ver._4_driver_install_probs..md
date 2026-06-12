---
title: "WPC54G Ver. 4 driver install probs."
date: 2006-09-01
forum: Networking &amp; Wireless
---

### Post by parliminux on 2006-09-01
I'm attempting to install the driver for the wpc54g ver. 4 card and I've gotten as far as downloading and trying to install via ndiswrapper.  Step by step: 
steve@valliegirl:~$ sudo ndiswrapper -i WPC54Gv4_dr
Installing wpc54gv4_dr
couldn't copy WPC54Gv4_dr at /usr/sbin/ndiswrapper line 135.

Has anyone got any clues or ideas as to why this is happening, and what I could do to fix it, or know what I may be doing wrong?
Any help is greatly appreciated.

---

### Post by yellerKat on 2006-09-01
WPC54Gv4_dr is a .zip file which needs to be expanded. The .inf file inside the .zip is the one which needs to be loaded (I think!)

---

