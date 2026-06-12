---
title: "Wierd graphical glitches (black bar) with an Intel graphics card on a Toshiba laptop"
date: 2011-05-06
forum: New to Ubuntu
---

### Post by ac0105 on 2011-05-06
Ever since updating to 11.04, I've had all sorts of video issues. I'm on  a Toshiba Satellite A305 with Intel Integrated Graphics.

The first time I rebooted Ubuntu, the login screen was a lower  resolution (1024x768 [with black bars] on the left and right side since  my laptop monitor is widescreen. I logged on and the main Unity desktop  was the same way. I went into the Monitor settings, changed it to  1280x800 (my normal resolution) and a big black vertical bar appeared on  the desktop. That spot on the desktop is "frozen" in that all the  windows that open over that area freeze there when you close them out.  The left side of the desktop is more so in the middle of the screen due  to this vertical bar.

I've rebooted a number of times and aside from one reboot, where it was  perfect, this black bar has appeared making my desktop useless. Any  ideas on what I can do or what might be causing this?

I am attaching a screenshot. Notice the left side of the screen where  all the closed firefox windows and other things are merged into each  other? Also, those icons near the middle of the screen should be on the  left side of my desktop, but due to this vertical bar, the desktop is  shifted to the right (and off screen).


Here is the info on my video card:[FONT=monospace]
[/FONT]     >                                                  00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series  Chipset Integrated Graphics Controller (rev 07)     Subsystem: Toshiba  America Info Systems Device ff1e     Kernel driver in use: i915      Kernel modules: i915           
Here is the package info on my intel driver
     >                                                  Package: xserver-xorg-video-intel Version: 2:2.14.0-4ubuntu7.1           
Any ideas?

---

### Post by Paddy Landau on 2011-05-06
I know that I originally had endless problems with my Toshiba laptop with its Intel graphics card. I eventually solved the problem by using an external monitor and not using the built-in one (so my laptop functions as a desktop -- it's not portable), and disabling Visual Effects.

I don't know how to disable Visual Effects effects in Unity, though.

Not terribly helpful, sorry, but I've seen other people have similar problems with Toshiba laptops. As good as the Toshiba machine is, the laptop screens have not given me a good experience.

---

