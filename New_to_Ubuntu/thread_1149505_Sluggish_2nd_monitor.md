---
title: "Sluggish 2nd monitor"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by vaughany on 2009-05-05
Hey all. I'm running Jaunty on my work laptop and am quite happy with it (I upgraded from Windows XP), however applications seem sluggish when used on my 2nd monitor. For example, if I scroll a page in Firefox or Open Office's word processor, the page is slow to update and you can see the redraw happening. This does not happen if you move the app to the main laptop screen.

The external (slow) screen's settings are 1024x768, and the main laptop's screen is set at 1280x800.

This could be a limitation of the computer: Intel graphics and a second monitor may not work together so well. I've checked on here and another post refers to using Synaptic to uninstall one set of video drivers and install another, so I checked and I seem to have a lot installed, and I'm wondering if that could be the cause?

The following are all installed (and I do mean installed, not just 'available to be installed' :)
xserver-xorg-video-s3
xserver-xorg-video-s3virge
xserver-xorg-video-v4l
xserver-xorg-video-mach64
xserver-xorg-video-r128
xserver-xorg-video-vesa
xserver-xorg-video-mach64-dbg
xserver-xorg-video-r128-dbg
xserver-xorg-video-nv
xserver-xorg-video-i128
xserver-xorg-video-sisusb
xserver-xorg-video-ati
xserver-xorg-video-tdfx
xserver-xorg-video-cirrus
xserver-xorg-video-i740
xserver-xorg-video-chips
xserver-xorg-video-trident
xserver-xorg-video-radeon-dbg
xserver-xorg-video-geode
xserver-xorg-video-apm
xserver-xorg-video-tseng
xserver-xorg-video-radeon
xserver-xorg-video-voodoo
xserver-xorg-video-ark
xserver-xorg-video-sis
xserver-xorg-video-neomagic
xserver-xorg-video-savage
xserver-xorg-video-siliconmotion
xserver-xorg-video-mga
xserver-xorg-video-vmware
xserver-xorg-video-ati-dbg
xserver-xorg-video-rendition
xserver-xorg-video-all
xserver-xorg-video-intel

Surely I don't need ATI divers for a Intel chipset...!! The docs mentioned the following may be useful:

$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

Sorry if this is a really n00b question (but at least I'm posting it in the right place!).

-Paul.

---

### Post by taseedorf on 2009-05-05
Try setting the "other monitor" as your main monitor... does this change anything? Is the notebook screen sluggish now?  Try also changing the fresh rates and make sure in your configuration you are not attempting to use the same settings for each monitor.  Can your video card handle two completely different configurations or is it only able to do clones?  Also, test using clone, extend and such and see if it makes a difference.  It could simply be a matter of configuration.

---

### Post by vaughany on 2009-05-05
> **taseedorf said:**
> Try setting the "other monitor" as your main monitor... does this change anything? Is the notebook screen sluggish now?

I dragged the monitors to they were arranged the other way around (in Display Prefs), I hope this is what you mean. When I did this, my panels moved to the external monitor and it worked like a charm, and my laptop's display became dog slow. So that has obviously had an effect.

> **taseedorf said:**
> Try also changing the fresh rates and make sure in your configuration you are not attempting to use the same settings for each monitor.

Each display has different pixel resolutions as mentioned in my first post but the refresh rates were different, although setting them the same (60Hz) makes no difference.

> **taseedorf said:**
>   Can your video card handle two completely different configurations or is it only able to do clones?

Laptop display: 1280x800 @ 60Hz; External monitor: 1280x768 @ 75Hz (now 60Hz).  It displays these just fine as long as you don't scroll! ;) These are the highest resolutions I am able to use with this laptop.

> **taseedorf said:**
> Also, test using clone, extend and such and see if it makes a difference.  It could simply be a matter of configuration.

Well the mirror checkbox works (tho using one set of settings on a 4:3 monitor and a 16:10 display is 'interesting' to say the least) but I'm not sure what you mean by clone, extend and such.

Thanks for the reply.

---

