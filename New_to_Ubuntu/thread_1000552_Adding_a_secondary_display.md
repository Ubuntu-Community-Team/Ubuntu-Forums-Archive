---
title: "Adding a secondary display"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by Calixte on 2008-12-03
I just bought a second LCD screen, and I'd like to use both displays. I tried **System > Preferences > Screen Resolution** and then clicked on **detect displays** but I get no reaction. I had no problem doing this on XP, so I know it isn't my hardware.

I do remember that there was a way to access another tool for changing resolution and using multiple screens, but I don't remember where I can find it.

Your help is much appreciated, thanks :-)


**PS:** I use Hardy, but I tried with the Intrepid Live CD with no more success.

---

### Post by realGaurab on 2008-12-03
I am using Intrepid and I can have no problem setting up my second monitor (flat panel LCD) on it. I do the same as you, go to System -> Preferences -> Screen Resolution and it automatically detects the second one and is ready for immediate use. 

Only thing is if I have compiz enabled, it asks me to log out and back in to enable the second monitor (don't know why). And when I need to go back to laptop alone, I will need to replace the xorg.conf in /etc/X11 with the original one and restart X (ctrl+alt+backspace) to get compiz back.

PS. My computer is a Acer Aspire 5630 and monitor is Acer X213WBD.

---

### Post by freak42 on 2008-12-03
what kind of gpu and gpu driver are you using ?
If you don't know then please attach the contents of the file /etc/X11/xorg.conf

---

### Post by Calixte on 2008-12-05
Monitors are both Samsung Syncmaster 743nx, graphics card is nVidia 7300. The driver is the proprietary one (I think).

Both screens show the ubuntu bootsplash, but the second goes black and is inactive when that part is finished.

Thanks for your concern,
 - Calixte

---

### Post by yellowaeroplane on 2008-12-05
If you are using the proprietary driver, try installing the package "nvidia-settings." It's a nice little program that does most of the work for you (including dual monitors). It definitely beats manually editing your xorg.conf file.

Try installing it with Synaptic and it will be under System>>Administration>>NVIDIA X Server Settings.

hope this helps a little at least!

---

### Post by jesterfred on 2009-11-17
Remember to run nvidia-settings as root or you will not be able to save your configuration.  (Or change the permissions on /etc/X11/xorg.conf)

---

