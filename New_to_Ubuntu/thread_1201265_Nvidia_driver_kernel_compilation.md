---
title: "Nvidia driver kernel compilation"
date: 2009-06-30
forum: New to Ubuntu
---

### Post by ncc1701e on 2009-06-30
While attempting to install the Nvidia driver 180.6 on my system, particularly during the phase where the installer is compiling a new kernel API, I get the following error:

ERROR: Unable to open /usr/lib/nvidia/libglx.xo.xserver-xorg-core

This is probably due to earlier when i was messing with removing references to the old driver to clean up the system for the new driver install.

does anyone know how I can re-install this file. or what package needs to be re installed?

thanks

---

### Post by ncc1701e on 2009-07-01
Sorry, just realized there was a typo in my ERROR messge here it is corrected:

ERROR: Unable to open /usr/lib/nvidia/libglx.so.xserver-xorg-core (No such file or directory)

I actually went into the directory as it seems there is something there by this name but I
think it is a link not the file itself.

---

