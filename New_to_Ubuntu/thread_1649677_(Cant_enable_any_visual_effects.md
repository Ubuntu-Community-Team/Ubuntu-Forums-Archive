---
title: ":(Cant enable any visual effects"
date: 2010-12-20
forum: New to Ubuntu
---

### Post by ghost95 on 2010-12-20
hi there can anyone help me enable visual effects i have a nvidia geforce 4 card?

---

### Post by Toxicbits on 2010-12-20
Did you enable the hardware drivers?

---

### Post by ghost95 on 2010-12-20
i think i have it has a green ball next to it:-s it does say it is activated!!!

---

### Post by JBAlaska on 2010-12-20
If your hardware drivers are installed and working, open a terminal and type: ```
compiz --replace
``` and note any error messages.

---

### Post by ghost95 on 2010-12-20
hi this is what it said

lib:  extension "GLX" missing on display ":0.0".
compiz (core) - Fatal: Root visual is not a GL visual
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

Launching fallback window manager

---

### Post by JBAlaska on 2010-12-20
It seems like your Nvidia driver is not installed correctly. Try going to **System, Administration, Nvidia X server settings** and check for errors and installed driver version.

---

### Post by ghost95 on 2010-12-20
it wont work i dont know what to do :'(

---

### Post by calavier62 on 2010-12-20
Have you installed the NVIDIA drivers, or are you using the generic ones that come with Ubuntu? Heres an easy way to check: go to the Software Center, and type in 'NVIDIA' in the search box. Make sure you have the Nvidia binary X.Org drivers installed.

---

### Post by sikander3786 on 2010-12-20
Which version of Ubuntu is there? Geforce 4 is a pretty old card and is no longer supported under Maverick.

[http://ubuntuforums.org/showthread.php?t=1592628](http://ubuntuforums.org/showthread.php?t=1592628)

You might want to use the open source Nouveau drivers that come with Maverick out of the box and I'm not sure of the Compiz success rate with those.

---

