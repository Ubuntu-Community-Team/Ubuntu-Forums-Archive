---
title: "triple images on screen-can't view images"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by rolypolycat on 2009-01-28
Hello!

I've installed both debian etch and regular ubuntu hardy, and had this problem both times. The installation goes alright, but when the login screen comes up, I have 3 of everything on most of the screen,save for the far left. I can't change it from the monitor menu on the monitor- an Envision- it justs auto-adjusts, or tells me a I need a particular resolution. That would be fine, but i can't see well enough to adjust it from a ubuntu menu or console. And the weird part- simplymepis has no trouble whatsoever displaying the right image. what does this distro have ubuntu doesn't? (And it's in xubuntu, too). I'm running on an old machine-3oomhz, and I'd really like to do a minimal install. Debian worked fine, but again, I got 3 images on the log-in screen. I can't do a minimal install in ubuntu; the installer can't find my hard drive, even though debian and simplymepis can.
Any help on this? Or the install problem? Thanks!

---

### Post by rolypolycat on 2009-01-29
bump:

Anybody have any ideas?

---

### Post by rolypolycat on 2009-02-26
Finally got Debian lenny to install. I had to do it as an alternate minimal install from the command line. 
after everything finished, I installed xorg. Then, before adding anything else, I opened the /etc/X11/xorg.conf file, and edited the monitor and screen sections to include my monitor's resolution, and commented out everything else but those settings. I saved the file, the added the rest of the software-file manager, window manager, etc. when it booted up, it booted to the resolutions in the xorg.conf file I added.
I never did figure out how to get a minimal install of xubuntu; it couldn't find the hard drives, but debian lenny and simplymepis had no trouble.

---

