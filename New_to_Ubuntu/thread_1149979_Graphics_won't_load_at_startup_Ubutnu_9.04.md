---
title: "Graphics won't load at startup Ubutnu 9.04"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by mattbutsko on 2009-05-05
Ubuntu has never failed me until now. Since I installed version 9.04 I've periodically lost the graphics layer of ubuntu suddenly. I may hit "Save" in GIMP and bam, I'm at the login screen.

That's not an issue, however, it happened again and now the graphics layer won't start. I get passed the login screen and am left at a black screen without a cursor.

I think the reason to this might be that I installed ATI's Catalyst Control Center; but I don't have the proprietary driver installed (not supported by the new kernel.) Could that be the source of ubuntu not starting properly? It is a graphics related issue, all in all.

I'm on the Live CD currently, and really need to save this system for a school project due.

Even if the ATI CCC isn't the issue, could I remove that via Live CD anyway? I really don't want it without the proprietary driver.

---

### Post by beastrace91 on 2009-05-05
A friend of mine is having a similar issue on Ubuntu 9.04, his GUI fails to load even when he installs the control center. I know he had to reformat to fix it, but try just removing the control center and see if that helps.

~Jeff

---

### Post by mattbutsko on 2009-05-05
That's what I'm trying to do, however I don't know the package name.

I can't find it in Synaptic on the Live CD and I Dr. Google doesn't know!

---

### Post by beastrace91 on 2009-05-05
Try ```
sudo apt-get remove --purge fglrx
``` Or if that packages is not installed try removing xorg-driver-fglrx with the same command, been awhile since I had ATI, headaches like this are the reason. Let me know if either of those work.

~Jeff

---

