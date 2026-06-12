---
title: "KDE error"
date: 2009-08-06
forum: New to Ubuntu
---

### Post by gianca81 on 2009-08-06
Hi all,

I have a problem with the KDE. I cannot load it and I have an error message:

(EE) xf860penSerial: Cannot open device /dev/input/wacom   No such file or directory
Error opening /dev/input/wacom : Invalid Argument
Synaptic DeviceInit called
SynapticCtrl called
Synaptic DeviceOn called
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from List!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from List!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from List!
Synaptic DeviceOff called
xinit: connection to X server lost

Anyone can help me?

Thanks a lot

bye

---

### Post by Favux on 2009-08-06
Hi gianca81,

Welcome to Ubuntu forums!

No answer yet?  I will give it a try.

What version of Kubuntu are you trying to start?  Is it 9.04 (Jaunty), 8.10 (Intrepid), or 8.04 (Hardy)?

Do you have a Wacom tablet?  Is it serial by any chance?

It may be a problem with your xorg.conf.  It is located in "/etc/X11/".  Could you post it?

---

### Post by Durden on 2009-08-06
It's trying to connect to your wacom tablet. If you don't have a wacom tablet then there is a problem with the config and we'll need to see it.

---

