---
title: "Compiz problem - Window decoration"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by waseq on 2009-01-11
Hi,
I ve got problem running Compiz.
Sometimes the window bar, where the name of program is, goes weired - changes color to some strange. It happens when I go with mouse over the closing (X) button or over the other two.

[IMG]http://waseq.webz.cz/trouble.png[/IMG]

I m using Ubuntu 8.10, default theme (but it happens also with the others), nVidia GeForce Go 7300, Compiz.

Could anyone help me?:confused:
Thanks

---

### Post by RomeReactor on 2009-01-11
Hi. Which version is your nVidia driver? Did you install it from the repositories or from nVidia's website? In 'System->Administration->Software Sources' go to the **Updates** tab and make sure the "Recommended updates" box is checked; then reload your package manager and search for the **nvidia-glx-180** driver and install it; that should solve the problem. If not, please post back.

---

### Post by waseq on 2009-01-23
Thanks, but there's something else now :(

I updated the nvidia driver to nvidia-glx-180. The window decoration is all right now. But the whole desktop is shifted slightly to the right. Small piece of the desktop and side bars, that is normally supposed to be on the right side of the screen, is now in the left part of the monitor. It's really weired. PrintScreen looks all right. It can be fixed by turning off all the special effects.

Any idea? With older driver it worked all right. :confused:

Thanks a lot

---

### Post by Therion on 2009-01-23
Bit of a longshot, but it's so simple it's worth trying...

Open CCSM and scroll down to the **Utilities** section.

Open up the plugin **Workarounds**.

DIS-able the check-box for "Legacy Fullscreen Support" and see if that helps.

---

### Post by waseq on 2009-01-24
I tried it but it has no effect. :(

---

