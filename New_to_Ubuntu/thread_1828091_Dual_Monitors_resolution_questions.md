---
title: "Dual Monitors resolution questions"
date: 2011-08-18
forum: New to Ubuntu
---

### Post by ArchaicAvenger on 2011-08-18
I'm new to Linux by a couple days now, and I've been trying to hook up my Compaq 5017m  monitor to my Toshiba laptop (not a netbook).  The laptop has a maximum resolution of 1280x800 and the external monitor 1024x768.  It worked perfectly when both monitors are on a resolution of 1024x768 (or any other combination lower than this for either screen), but it lags when I try to put the laptop on maximum.

This laptop was Windows a week ago and it had no problem supporting both monitors at peak resolution, so I don't think it would be the graphics card.  I am running Ubuntu 11.04.  Is there a driver I need to install, or a setting I need to tweak?  (And if so, how?)

---

### Post by seawolf167 on 2011-08-18
See if you have any video drivers available to install. Assuming you are using 11.04, click the power button in the upper right, select system settings, then select Additional Drivers and check for graphics drivers.

---

### Post by ArchaicAvenger on 2011-08-18
No drivers to install.  (And yes, it's 11.04).

I saw [an earlier thread]("http://ubuntuforums.org/showthread.php?t=1809560&highlight=dual+monitors") with a similar (if not the same) problem, and one of the suggestions was to edit Xorg.conf to force a specific resolution.  Is that something that would work (and if so, how would I do it?)

---

### Post by seawolf167 on 2011-08-18
Take a look at [this how-to page ]("https://wiki.ubuntu.com/X/Config/Resolution#How_to_setup_a_dual_monitor")for manually setting it with xrandr/xorg/etc.

---

### Post by ArchaicAvenger on 2011-08-18
Looked over the link and tested out several commands, but I'm still essentially having the same problem.  I can get the screens to the correct resolutions (I started with both the screens on and both at the resolution 1024x768, then used the command "xrandr --output LVDS1 --mode 1280x800 --rate60"), but then there's this strange overlap in between them that fills in the space that was just black on the larger screen when it was set to a lower resolution.  On the Monitors panel under System Settings, the diagram literally showed the external monitor screen as on top of the laptop screen for a few inches on the right side.  When I moved the external monitor screen off the laptop and fully to its right (whether through the System Settings menu, or through a terminal command) it puts me right back with the same problem of it lagging and the desktop being a black page.

---

### Post by abish on 2011-08-18
I had similar problem with using a projector. Then i found 'resolution switcher' aka resapplet. It stays in the taskbar, and with a drop down menu, you can switch the resolution that fits best in the external display.

sudo apt-get install resapplet

give it a try.

---

### Post by ArchaicAvenger on 2011-08-18
I'm trying that right now, but it's not changing the problem I'm having.  It says online it uses prewritten settings in the xorg.conf, and I don't have anything written there.

---

