---
title: "How do I enable com?piz in Kubuntu?"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by diablo75 on 2008-12-21
Dumb question of the night:

I've not used Kubuntu really... at all.  I've been using GNOME for the last three years and I'm liking the way KDE looks right now.  How do I enable compiz/Desktop Effects in Kubuntu?

---

### Post by evilkastel on 2008-12-21
they are not by default. you have to install the package from adept. compiz-fusion and all the dependencies. also ccsm. then you enable it as regular.

---

### Post by diablo75 on 2008-12-21
How do I enable it?

---

### Post by Xiong Chiamiov on 2008-12-21
KDE4 has desktop effects built-in, as part of kwin.  If you prefer to use Compiz for whatever reason, a "compiz --replace" should do the trick; I'm not sure how to enable it by default.

---

### Post by igknighted on 2008-12-21
The best would be to install the fusion-icon program and add it to your kde autostart folder (~/.kde/Autostart).

However, most compiz effects (wobbly windows, cube, fade in/out, etc.) are built into KDE.  You can enable them in System Settings -> Desktop.  The KDE effects are much more stable, and usually much less resource intensive.

---

### Post by The Recorder on 2008-12-22
Go to "System Settings" - Open up "Default Applications" - The last item on the left is "Window Manager" - Click on it, and choose "Use a different widow manager" (on the right hand side, under "Default Component"), and choose "Compiz" from the dropdown list.

---

### Post by michwill on 2009-01-10
> **igknighted said:**
> 
However, most compiz effects (wobbly windows, cube, fade in/out, etc.) are built into KDE.  You can enable them in System Settings -> Desktop.  The KDE effects are much more stable, and usually much less resource intensive.


Are you sure about that?  I've tried configuring KDE 4.1 to use the cube and it's simply not there by default -- nor can I seem to enable it properly.  I'm using the latest version of Kubuntu 8.10 as of this post date with kernel 2.6.27-9-generic.  I've also installed the latest 

FYI, I've tried both 32-bit and 64-bit Kubuntu installs.


System Specs:
Gigabyte MA790X-DS4
2 GB DDR2 667
AMD X2 4600+
PNY GeForce 6600 PCI-E

Nvidia Driver:
Version: 180.22
Operating System: Linux x86
Release Date: January 8, 2009

---

