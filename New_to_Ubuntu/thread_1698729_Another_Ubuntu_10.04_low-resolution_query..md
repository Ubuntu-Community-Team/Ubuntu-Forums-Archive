---
title: "Another Ubuntu 10.04 low-resolution query."
date: 2011-03-02
forum: New to Ubuntu
---

### Post by Cap'n Redbeard on 2011-03-02
Hi Folks,

i've just installed Ubuntu 10.04 and the System-Preferences-Monitors panel will allow me no greater display resolution than 800 x 600.

> ~$ xrandr

tells me:

> xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  
   400x300        60.0     56.0  
   320x240        60.0 


> ~$ lspci | grep VGA

tells me:

> 01:00.0 VGA compatible controller: Trident Microsystems CyberBlade/i1 (rev 6a)

and

> ~$ sudo lshw -C video

tells me:

>   *-display UNCLAIMED     
       description: VGA compatible controller
       product: CyberBlade/i1
       vendor: Trident Microsystems
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 6a
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-2.0 pm bus_master cap_list
       configuration: latency=32
       resources: memory:e5800000-e5ffffff memory:e6000000-e601ffff memory:e5000000-e57fffff memory:20000000-2000ffff(prefetchable)


This is an old VIA BN860T micro-atx motherboard with built-in VIA VT8601T video hardware. Quite capable of 1280 x 1024 display resolution (it runs quite happily at this setting in windoze XP Professional).

A few years ago, running Ubuntu 8.04 i encountered a similar problem which was easily resolved by:

> ~$ gksu displayconfig-gtk

Is there anything like this in Ubuntu 10.04 ?

No drivers are available for this chip-set from VIA, the nearest they have is their "xf86-video-unichrome" drivers for more recent chips and they don't compile properly.

What am i doing wrong ?

:(

---

### Post by davidmohammed on 2011-03-02
I think you'll need to force the use of the trident driver.

Try to create an xorg.conf file similar to [this post]("http://kubuntuforums.net/forums/index.php?topic=3099842.15").

At a guess you'll need to add the following (or similar) to xorg.conf

```
Section "Device"
   Identifier   "Trident Microsystems CyberBlade/i1"
   Driver      "trident"
   BusID      "PCI:1:0:0"
EndSection

Section "Monitor"
   Identifier   "Generic Monitor"
   Option      "DPMS"
   HorizSync   28-51
   VertRefresh   43-60
EndSection

Section "Screen"
   Identifier   "Default Screen"
   Device      "Trident Microsystems CyberBlade/i1"
   Monitor      "Generic Monitor"
   DefaultDepth   24
   SubSection "Display"
      Modes      "1024x768"
   EndSubSection
EndSection

```

---

### Post by Cap'n Redbeard on 2011-03-02
Hey davidmohammed,

Fantastc. That works !

i just remarked out the existing "Device", "Monitor" and "Screen" sections of xorg.conf and pasted in your excerpt from above. That worked fine, giving 1024x768 resolution.

Have just modified xorg.conf again thus:

> Section "Device"
   Identifier   "Trident Microsystems CyberBlade/i1"
   Driver      "trident"
   BusID      "PCI:1:0:0"
EndSection

Section "Monitor"
   Identifier   "Generic Monitor"
   Option      "DPMS"
   HorizSync   30-81
   VertRefresh   56-75
EndSection

Section "Screen"
   Identifier   "Default Screen"
   Device      "Trident Microsystems CyberBlade/i1"
   Monitor      "Generic Monitor"
   DefaultDepth   24
   SubSection "Display"
      Modes      "1024x768" "1280x1024"
   EndSubSection
EndSection


to set the right sync and refresh rates for this monitor and added the "1280x1024" mode and the System-Preferences-Monitors panel now shows all display resolutions up to 1280x1024.

Well done mate. i'd better mark this thread as "solved",

Cheers,

---

