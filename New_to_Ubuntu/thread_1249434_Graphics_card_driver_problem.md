---
title: "Graphics card driver problem"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by designateduser on 2009-08-25
So after finding the default graphics on Ubuntu 9.04 kind of boring I decided to try and find the driver for my graphics card (ATI Radion HD3000) so I could enable visual effects, and maybe even have my dock (cario-dock) work in a more pleasing manor. I downloaded off the ATI/AMD website the driver for linux and followed their instructions for install. After the install was successful I checked under System>adm>Hardware drivers to see if it had popped up, it had not, but just in case maybe it had installed anyway I tried to enable visual effects (System>Pref>Appearance) and my computer left gnome and went to the regular font-only mode. It was no big deal untill it didn't move for a while. I assumed maybe it was like terminal and responded to BASH but alas, after a min or so of trying escape commands it would not leave. So I was forced to power down my computer. How can I get this driver working?

---

### Post by halitech on 2009-08-25
after you finished the install, did you run
```
aticonfig --initial
```

---

### Post by designateduser on 2009-08-25
Just tried that, it issued:
Found fglrx primary device section
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-0
aticonfig: Writing to '/etc/X11/xorg.conf' failed. Bad file descriptor.

---

### Post by halitech on 2009-08-25
run it as sudo, I forgot it needs to write outside /home

---

### Post by LowSky on 2009-08-25
sudo aticonfig --initial

---

### Post by designateduser on 2009-08-25
I got:
cody@cody-laptop:~$ sudo aticonfig --initial
[sudo] password for cody: 
Found fglrx primary device section
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-0

success?

---

### Post by designateduser on 2009-08-25
tried to enable visual effects again, still no dice, but it didn't leave gnome. it just said "visual effects could not be enabled" and the ATI driver is still not showing up in System>Adm>Hardware drivers.

---

### Post by halitech on 2009-08-25
the driver won't show up in hardware drivers 

not sure why its still saying cannot enable the visual effects. maybe try a reboot to force the new drivers to be seen

---

### Post by designateduser on 2009-08-25
restarted and no luck I got "Desktop effects could not be enabled" and my Hardware drivers still don't have ATI Radeon listed, however, **under "applications" a new heading called ATI catalyst control center is listed. **

---

### Post by halitech on 2009-08-25
the hardware drivers won't be listed under hardware drivers as you did not install anything from Ubuntu

not sure why the desktop effects are still not working. Look around the ATI control center and see if there are some settings there you need to tweak to get it working

---

### Post by designateduser on 2009-08-25
I have been tweaking around and still no dice, but I just thought, I think the installer documentation mentioned having some programs installed or something? maybe I need a peripheral for it to work?
from ATI intaller documentation:
"The following packages must be installed in order for the CatalystTM Linux driver to
install and work properly:
    XFree86-Mesa-libGL
    libstdc++
    libgcc
    XFree86-libs
    fontconfig
    freetype
    zlib
    gcc

---

### Post by halitech on 2009-08-25
if the programs weren't installed then the catalyst driver wouldn't have worked

---

### Post by Mark Phelps on 2009-08-25
> **designateduser said:**
> I have been tweaking around and still no dice, but I just thought, I think the installer documentation mentioned having some programs installed or something? maybe I need a peripheral for it to work?
from ATI intaller documentation:
"The following packages must be installed in order for the CatalystTM Linux driver to
install and work properly:
    XFree86-Mesa-libGL
    libstdc++
    libgcc
    XFree86-libs
    fontconfig
    freetype
    zlib
    gcc

These are only needed if you're going to compile the driver yourself -- which you're not.

As Halitech has said, if you're seeing the Catalyst Control Center, the ATI app and drivers got installed.

To confirm that for yourself, enter "fglrxinfo" from a terminal.  That's the ATI restricted driver.  You will see if it's not installed.

---

### Post by designateduser on 2009-08-25
It's installed! But for some reason I am still not able to enable desktop effects...hmmmm :(

---

### Post by fransor on 2009-08-25
Is there anyone who know how to get drivers for Intel GMA500? I´m VERY beginner of this...

---

