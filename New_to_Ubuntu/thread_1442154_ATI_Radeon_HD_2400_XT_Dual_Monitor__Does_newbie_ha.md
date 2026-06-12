---
title: "ATI Radeon HD 2400 XT Dual Monitor  Does newbie have a chance?"
date: 2010-03-29
forum: New to Ubuntu
---

### Post by RH9R on 2010-03-29
Hours of forum searches make the dual monitor setup look out of reach for the newb. 'Running a Dell optiplex 755 w/ Radeon HD 2400 XT R610 and a fresh install of Karmic (until the next LTS).

 lspci|grep VGA

01:00.0 VGA compatible controller: ATI Technologies Inc RV610 [Radeon HD 2400 XT]

 xrandr

Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 1280 x 1280

DVI-1 disconnected (normal left inverted right x axis y axis)

DVI-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 376mm x 301mm

   1280x1024      60.0*+   75.0     60.0* 

   1152x864       75.0  

   1024x768       75.0     60.0  

   800x600        75.0     60.3  

   640x480        75.0     59.9  

   720x400        70.1  

I don't care about 3d, just want the screen real estate. Is this just not in the cards? I'd sure appreciate any help getting the large desktop working. Many Thanks.

---

### Post by ajgreeny on 2010-03-29
Try editing the /etc/X11/xorg.conf file manually.  You may have to actually make such a file first, as it is not present any more by default, so try ```
gksudo gedit /etc/X11/xorg.conf 
```and either put your version of the following into the empty file, or edit what is already there with your version of thi, ie with your own refresh rates and required resolutions.
```
Section "Device"
    Identifier     "Configured Video Device"
    Driver         "ati"
EndSection 

Section "Monitor"
    Identifier    "Configured Monitor"
            HorizSync    30-80
            VertRefresh    50-75
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    16
    SubSection "Display"
        Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

```

Note that I use 16 bit colour to get compiz to work, but you may be OK with 24 bit; try it out and see.

---

### Post by RH9R on 2010-03-29
ajgreeny. 'Can't say how much I appreciate your kind help. I'm looking up screen stats (synb/refresh) and trying to execute the .conf file now. 
 
I so appreciate your kind help.

---

### Post by readycarpenter on 2010-03-29
did you install the proprietary drivers? via ? 

system>admin>hardware divers

this will make everything easier

---

### Post by RH9R on 2010-03-29
Hi ajgreeny,
 
applied settings. 'Still only left monitor appears. 
'Went to display, unclicked 'mirror' and now left monitor lights up, but has no desktop - just blank background.
Again, I appreciate your help.

---

### Post by ajgreeny on 2010-03-30
OK, try the 16 bit colour as in my xorg.conf.  That may give you a background back, or just run without compiz (Alt+F2, enter metacity --replace).

---

### Post by tom.gobel on 2010-03-30
I was having a bit of trouble trying to extend my desktop in that the external monitor would mirror the primary, but would not function as an extension.

I was able to solve the issue by setting the 'Visual Effects' option to None.

System > Preferences > Appearances : Visual Effects tab - select None.

---

### Post by Mark Phelps on 2010-03-30
> **readycarpenter said:**
> did you install the proprietary drivers? via ? 

system>admin>hardware divers

this will make everything easier

Not if there aren't any!! ATI dropped Linux support for this card over a year ago.  Forcing an install of the ATI drivers is only going to trash their display and force them to do a lot of work cleaning up the mess they made.

---

### Post by RH9R on 2010-03-30
Ready, Aj, Tom & Mark. Thank You!
 
I tried loading the proprietary driver from the icon at the top - at least 4 times w/ diff options. No joy. Another forum post said it didn't work, so I tried loading manually w/ no better result. Effects are turned off immediately after loading the system, and apci=off is in the load script.
 
This morn, I tried loading Hardy & following some forum paths, but no luck so far. I'll try the icon load of the ati prop. driver w/ Hardy now. I will include colors = 16 if there's no joy at 24 (thx AJ). 
 
If any of the new attempts work, I'll post what did work. Again, many thanks to each of you.

---

