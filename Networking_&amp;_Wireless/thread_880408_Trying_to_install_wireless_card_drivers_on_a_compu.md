---
title: "Trying to install wireless card drivers on a computer with no internet."
date: 2008-08-05
forum: Networking &amp; Wireless
---

### Post by regoob on 2008-08-05
This is my first time trying to run Linux on my machine and I am in a bit of a pickle. I do not have an ethernet card on my computer (long story) but I do have a DWA-552 D-Link Wireless N card. I am currently trying to install some of the drivers onto my computer by using a CD and downloading them from another computer and putting them on mine. But, the only drivers that are available for my wireless card are Windows based, so I tried installing Wine and all its dependencies, but got an error message. So, what should I do now? Thanks.

---

### Post by nittybitty on 2008-08-05
Are you dual booting? If so, the drivers should be in the windows partition if you have access to it.

The alternative is to put the drivers on a thumb drive and install from there.

The other alternative is a wired connection (via some pcmcia card since you don't have ethernet) to download the drivers.

From there, installing in Gnome should be a snap.

Under KDE, I am baffled - I cannot figure out how to install drivers for a specific piece of hardware.

The problem you are having is common and it is unfortunate the major releases don't deal resolving this in a more user friendly way.

For instance, if there is a piece of hardware that is missing a driver, how about making it easy to install the missing driver so it can be installed? Duh. Windows figured this out in version 3.x

Good luck, especially if you are attempting this under KDE!!!

---

