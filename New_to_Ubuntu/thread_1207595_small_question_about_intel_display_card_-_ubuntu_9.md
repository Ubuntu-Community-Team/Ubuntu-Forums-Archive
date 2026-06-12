---
title: "small question about intel display card - ubuntu 9.04"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by psfelgate on 2009-07-08
Good day

I'm hoping someone can help. I'm using an onboard i915 display card (laptop is IBM R50e) but it seems that the display is a bit "jerky" eg. when moving a window it lags a bit as you can see multiple trails of the window  behind it trying to catch up (you know what I mean :P).

Yet running glxinfo shows me "direct rendering: yes".

So why does it still lag? surely the drivers are installed? or is there something that I must "tweak" to get the full potential of the card?

---

### Post by prshah on 2009-07-08
> **psfelgate said:**
> 
running glxinfo shows me "direct rendering: yes".

So why does it still lag? surely the drivers are installed? or is there something that I must "tweak" to get the full potential of the card?

It is not enough that direct rendering is enabled; if you are using a software renderer, then you may get the effect described. glxinfo will tell you which renderer is in use.

There are a number of "tweak" parameters for intel chipset graphics. For example, if you are using EXA acceleration, setting "MigrationHeuristic" to "greedy" will greatly improve performance. For intel chipsets, three types of acceleration are available: XAA (old), EXA (stable), and DRI2/UXA (experimental and brand new). To check which acceleration you are using, open a terminal (Applications-Accessories-Terminal) and post the output of ```
cat /var/log/Xorg.0.log | grep -i accel
```

Some people say the adding of an environment variable INTEL_BATCH helps performance. You can test it and see if you find a performance improvement with glxgears```

glxgears
INTEL_BATCH=1 glxgears

``` and compare the outputs of each.. do you find any substantial difference in the framerates?

---

### Post by binbash on 2009-07-08
Switch to UXA : 

[http://www.ubuntu-inside.me/2009/03/how-to-enable-uxa-at-ubuntu-jaunty.html](http://www.ubuntu-inside.me/2009/03/how-to-enable-uxa-at-ubuntu-jaunty.html)

---

### Post by psfelgate on 2009-07-09
Ok, so

```
cat /var/log/Xorg.0.log | grep -i accel
```

gives me:

```
(==) intel(0): Using EXA for acceleration
(II)         Composite (RENDER acceleration)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(**) TPPS/2 IBM TrackPoint: (accel) keeping acceleration scheme 1
(**) TPPS/2 IBM TrackPoint: (accel) filter chain progression: 2.00
(**) TPPS/2 IBM TrackPoint: (accel) filter stage 0: 20.00 ms
(**) TPPS/2 IBM TrackPoint: (accel) set acceleration profile 0
(**) Darfon USB Optical Mouse: (accel) keeping acceleration scheme 1
(**) Darfon USB Optical Mouse: (accel) filter chain progression: 2.00
(**) Darfon USB Optical Mouse: (accel) filter stage 0: 20.00 ms
(**) Darfon USB Optical Mouse: (accel) set acceleration profile 0

```

So I guess I am using exa for acceleration? I'm gonna try the uxa as mentioned above and see how that goes...

EDIT: Using uxa still makes no difference :(

---

### Post by prshah on 2009-07-09
> **psfelgate said:**
> 
```
(==) intel(0): Using EXA for acceleration
(II)         Composite (RENDER acceleration)

EDIT: Using uxa still makes no difference :(

How did you try to enable UXA (exact steps)? I hope you restarted X after making the changes to enable UXA.

Alternately, try this (for EXA acceleration, no use for others); In the xorg.conf device section for "Configured Video Device", add / edit the two lines below in red. Also add the lines in blue if you want Ctrl+Alt+BkSpace to restart X[code]Section "Device"
        Identifier      "Configured Video Device"
[color=red]        Option  "AccelMethod"   "EXA"
        Option  "MigrationHeuristic"    "Greedy"[/color]
        #       Option  "AccelMethod"   "UXA"
EndSection

[color=blue]Section "ServerFlags"
        Option  "DontZap"       "false"
EndSection
[/color]
```

Don't forget to comment out the UXA acceleration line if enabled. Then, save and exit. Restart X; any performance improvement? If not, check if your new options have taken effect and are not being overridden```
cat /var/log/Xorg.0.log | grep -i -E accel\|greedy
```

Note that while UXA is supposedly to give better performance, I find EXA/greedy works much better on my Fujitsu laptop's Intel 855GM device.

---

### Post by Paqman on 2009-07-09
To be honest, the easiest solution for Intel users is probably just to use Intrepid for now. Karmic will be out in a few months and should have the problem fixed. Intrepid is still fully supported.

---

### Post by psfelgate on 2009-07-09
Ok this is now my xorg.conf file:

```

Section "Device"
	Identifier	"Configured Video Device"
	Option	"MigrationHeuristic"	"greedy"
	Option	"AccelMethod"	"exa"
	Driver	"intel"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerFlags"
	Option	"DontZap"	"off"
EndSection

```

It seems a bit faster but theres still that "lag" especially while dragging a windows thats on top of another window.

Is there maybe a way to disable showing the window contents while dragging like on windows?

---

