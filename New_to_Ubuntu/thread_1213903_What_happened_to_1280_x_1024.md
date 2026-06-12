---
title: "What happened to 1280 x 1024 ??????"
date: 2009-07-15
forum: New to Ubuntu
---

### Post by mistypotato on 2009-07-15
Everything seems to be working EXCEPT I no longer have the option of setting resolution to 1280 x 1024 ???

That is the setting I have always used until today.  Now it's gone...vanished...like it never was an option?

768 appears to be the highest available horizontal res I have available yet until today I had always used 1280 x 1024.

I'm using a nvidia 9600gtx graphics card on a HP f1703 monitor (unchanged since last year).  Driver is nvidia version 180 (activated).

Another wierd problem....when the browser is open (like now) the controls to minimize/maximize/close are no longer there.  I have to Alt-Tab to close the browser or navigate away.

Anyone know what's wrong?

---

### Post by guitar_man on 2009-07-15
are the drivers for the card installed???

---

### Post by mistypotato on 2009-07-15
Yes.

Driver is nvidia version 180 (activated).

I uninstalled and reinstalled but no go.   Still can't get 1280 x 1024.

---

### Post by Mauricio1 on 2009-07-15
Update Ubuntu with this: Click System, Click Administration and Update manager to be sure you have de actual driver for you video card, Restart and then check System, Preference, Display to change the resolution that you want.

---

### Post by mistypotato on 2009-07-15
Well,

This machine is a dual booter so I booted into WinXP and guess what?

I get 1280 x 1024 there with no problem so it isn't hardware.

---

### Post by mistypotato on 2009-07-15
Well,

I solved this one on my own.

I kept fiddling with the xorg.conf file, hunting with Google until I found a config that matched my hardware and then made several changes to my own xorg.conf and to my total shock, it was back to normal after a reboot.

I have no clue why things changed in the forst place but I'm going to make a backup copy of that file right away and save it somewhere.

If you're having similar problems, I can say that you should carefully study the SCREEN, DEVICE and MONITOR sections carefully and get a feel for what they are doing and how they work.

Fixing my issue occurred very soon after I understood how that file was organized and how it worked.   It looks complicated, but it's not really that much so.

Here's what it looks like now (working again)....
Section "Monitor"
     # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "HP"
    ModelName      "hp f1703"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Screen"
	Identifier	"Screen0"
	Monitor		"Monitor0"
	Device		"Device0"
	DefaultDepth	24
    SubSection "Display"
        Modes "1280x1024" "1024x768" "800x600"
    EndSubSection
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9800 GT"
    BusID          "PCI:1:0:0"
    Screen          0
    Option "MonitorLayout" "DFP, CRT"
EndSection


That's it !!

One small side note...
There WAS an entry in there with something about GLX...but I didnt know what it was so I deleted it.   Maybe that helped too?   I dunno about that part?

---

