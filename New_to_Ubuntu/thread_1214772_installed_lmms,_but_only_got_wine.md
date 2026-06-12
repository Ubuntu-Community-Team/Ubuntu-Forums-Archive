---
title: "installed lmms, but only got wine"
date: 2009-07-16
forum: New to Ubuntu
---

### Post by drunk-wolf on 2009-07-16
I heard that LMMS was a good linux replacement for FLstudio, so I went into synaptic and installed it, but when I looked through applications afterward all that it installed was Wine, now I don't mind the wine install, but I can't find where LMMS installed to, is there something I'm missing, or is this a bug?? running intrepid.

---

### Post by drunk-wolf on 2009-07-16
anybody?? I'd really like to get this working, and why is it always such a PITA to install new software on linux, this is the third time in a month that Synaptic hasn't worked properly...

---

### Post by eMJayy on 2009-07-16
> **drunk-wolf said:**
> I heard that LMMS was a good linux replacement for FLstudio, so I went into synaptic and installed it, but when I looked through applications afterward all that it installed was Wine, now I don't mind the wine install, but I can't find where LMMS installed to, is there something I'm missing, or is this a bug?? running intrepid.

At one point last year I installed LMMS on my PC and I had the same issue. It's installed, but it's not listed in the applications menu for some reason. I think, if my memory serves me correctly, that the installation created a folder in your home directory (called LMMS, i think), You should be able to run it from that folder. I'm going to install it again on this PC - i didn't really get around to trying it out the last time.

---

### Post by eMJayy on 2009-07-16
Ok, I have it installed now. 

Noticed a few things. First, if you install support for VST plug-ins it installs wine. Apparently, those plug-ins will only run in Wine. I didn't bother to add that support to the installation. 

Second, I found the program installed in Applications - it added an icon inside *Sound & Video* ...look for **Linux Multimedia Studio **, which is the full name of the application.

---

### Post by drunk-wolf on 2009-07-16
finally found it in filesystem/usr/bin/lmms, still nothing in sound and video, ended up using "sudo which lmms" to find it

---

