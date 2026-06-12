---
title: "Help with video drivers!"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by Famine on 2009-02-25
Hey guys, I have installed Ubuntu onto my PC, but I am having troubles with the video drivers.  I am using an nvidia 6600 video card, and when I goto install the drivers for it, I choose the recommended ones, it downloads and installs, then says I need to restart for the drivers to take effect.  Anyway I restart, the Ubuntu loading screen comes up, and when its about to boot into the login screen, I get no video (monitor goes to sleep mode).  I get video perfectly without the drivers (But cannot set the resolution I would like).  I have reinstalled ubuntu thinking it might work a second time around but I get the exact same thing.  Now I am stuck, because I have no interface to work with at all, the screen is still blank.

Also, I cannot RDP into the ubuntu box either.  It will not respond.

Any ideas??

---

### Post by taurus on 2009-02-25
Which drivers have you installed so far?  I have a 6800XT card and I use version 177 with no problem at all.

---

### Post by Famine on 2009-02-25
I did the recommended one, which was 177.

I want to remove it using this command in the recovery console:

apt-get remove --purge *package name*

But I dont know the name of the nvidia driver package.  Any ideas?

---

### Post by taurus on 2009-02-25
Probably something like nvidia-glx-177.

---

### Post by Famine on 2009-02-25
Ok, back into ubuntu using:

apt-get remove --purge nvidia-glx-177

dpkg-reconfigure xserver-xorg -phigh

reboot


Now to find drivers that work...

---

### Post by Famine on 2009-02-25
Installed 173 drivers, exact same thing happened. :(

Is there any way to increase the resolution manually?  It only goes up to 800x600 in the list.

---

### Post by taurus on 2009-02-25
Are you using the generic nv driver?  Look in synaptic for envy package and install it.  Then, see if envy would install a working nvidia driver for your graphic card.

---

### Post by Famine on 2009-02-25
Will do, installing envy now.  Thanks.

---

### Post by Famine on 2009-02-26
Same thing....  Tried a different video card and it worked perfectly though.  Thats really strange because I was using the 6600 on a windows machine with no problems at all :S

---

