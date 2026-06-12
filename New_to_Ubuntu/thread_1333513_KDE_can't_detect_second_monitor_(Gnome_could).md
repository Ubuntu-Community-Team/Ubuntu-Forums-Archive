---
title: "KDE can't detect second monitor (Gnome could)"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by rburbrid on 2009-11-21
Hey,

I've looked all over but can't find the answer... Hopefully someone here can help =)

I switched to Ubuntu about 3 years ago (100%) and have dual display.  Gnome has always detected them pretty easily (or at least I could find a tutorial or something that showed me how).  With Karmic, I switched to KDE (Kubuntu).  It's a fresh installation (not upgrade) and I formatted my hdd completely (letting the installer pick the partitioning scheme).

The problem is, KDE can't detect my second (DVI) display!  When I go to System Settings > Computer Administration > Display > Multiple Monitors, I just get the message 
[INDENT][FONT="Courier New"]This module is only for configuring systems with a single desktop spread across multiple monitors.  You do not appear to have this configuration.[/FONT][/INDENT]
This is exactly the configuration I used to have, and is the configuration I'd like!  

when I go to System Settings > Computer Administration > Display > Size & Orientation, it only shows one monitor, even when I do "Identify Outputs."
This worked for me with Ubuntu Karmic (Gnome) before I switched to KDE.

I used Compiz(-Fusion) in Gnome to accomplish this to some extent, and when I had to set it up before, I used "TwinView", but can't seem to find a tutorial on how to set it up for KDE. 

I'm not much of a hardware guy, so hopefully this should be easy for some guru to set me straight.  Thanks!

**UPDATE!** Solved!  The thing I had forgotten was that my video card is nvidia, so I had to use the nvidia-settings program (sudo nvidia-settings).  That allowed me to detect and enable the second monitor.  Thanks =)

---

### Post by vidak on 2009-12-02
I have the same problem. A workaround can be xrandr. Try to run xrandr from console, you'll see the available displays (VGA1 and LVDS1 at me). Run 
xrandr --output VGA1 --auto 
to enable the second display, then
xrandr --output VGA1 --left-of LVDS1
(or whatever the physical position of the two monitors are) for dual-head.
Hope this helps.

---

### Post by amit223comp on 2011-04-25
Hi,
 

I also faced the same problem on 10.04 (Lucid) , the above solution worked for me . Thanks :D

sudo xrandr --output DVI-0 --auto

 sudo xrandr --output DVI-0 --left-of   DVI-1


-Amit

---

