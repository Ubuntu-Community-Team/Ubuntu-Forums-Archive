---
title: "touch pad configuration in xubuntu"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by sellyoursoulformusic on 2009-01-17
i'm looking to turn off tap to click and set the scroll area width on my touch pad.  i didn't see a gui for changing touch pad settings so i used synaptic package manager to install gsynaptic.  i still don't see any gui for changing touch pad settings.  i'm a lost windows user at this point.  what should i be looking for here?  

xubuntu seems pretty snazzy...if i can just figure out what i'm doing.

---

### Post by sellyoursoulformusic on 2009-01-17
i'm trying to follow this page:  [https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig](https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig)

i don't have a shmconfig.fdi file here.  can i just create the file and add the necessary lines?

---

### Post by sellyoursoulformusic on 2009-01-17
i tried creating shmconfig.fdi, but got the error message 'can't open file to write'.

am i in the right forum for help with this problem?

---

### Post by sellyoursoulformusic on 2009-01-17
*bump*

any ideas at all?

---

### Post by sellyoursoulformusic on 2009-01-18
i got some help with turning off 'tap to click' in another forum.  i'm just passing along the solution for other noobs (thanks to castlerock for the help).  i added these four lines to the xorg.conf file, located at etc/X11.  here's how i did it.

1. open a terminal and type:  sudo *yourtexteditor* 

the text editor installed by default on my machine was mousepad so i typed:  sudo mousepad

2. navigate to and open etc/X11/xorg.conf with your now opened text editor.

3. add four lines to xorg.conf.  here's what the section of xorg.conf looked like before adding the lines:

```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
        
EndSection   
``` 

and after

```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
        Option          "MaxTapTime" "0"
        Option         "TapButton1" "0"
        Option         "TapButton2" "0"
        Option         "TapButton3" "0"
EndSection
```

---

### Post by treesurf on 2009-01-18
Perhaps this thread will help:
[http://ubuntuforums.org/showthread.php?t=1027092&highlight=touchpad+scrolling](http://ubuntuforums.org/showthread.php?t=1027092&highlight=touchpad+scrolling)

Also see this for changing the scroll area:
[http://blog.eddiemonge.com/2008/08/03/scrolling-area-adjustment-for-touchpads-using-ubuntu/](http://blog.eddiemonge.com/2008/08/03/scrolling-area-adjustment-for-touchpads-using-ubuntu/)

---

### Post by sellyoursoulformusic on 2009-01-18
> **treesurf said:**
> Perhaps this thread will help:
[http://ubuntuforums.org/showthread.php?t=1027092&highlight=touchpad+scrolling](http://ubuntuforums.org/showthread.php?t=1027092&highlight=touchpad+scrolling)

Also see this for changing the scroll area:
[http://blog.eddiemonge.com/2008/08/03/scrolling-area-adjustment-for-touchpads-using-ubuntu/](http://blog.eddiemonge.com/2008/08/03/scrolling-area-adjustment-for-touchpads-using-ubuntu/)

hey treesurf, i tried both of those methods, but  neither worked here.  i'd still like to change the scroll area width on my touchpad.  back to the search.

---

### Post by sellyoursoulformusic on 2009-01-18
> **sellyoursoulformusic said:**
> i got some help with turning off 'tap to click' in another forum.  i'm just passing along the solution for other noobs (thanks to castlerock for the help).  i added these four lines to the xorg.conf file, located at etc/X11.  here's how i did it.

1. open a terminal and type:  sudo *yourtexteditor* 

the text editor installed by default on my machine was mousepad so i typed:  sudo mousepad

2. navigate to and open etc/X11/xorg.conf with your now opened text editor.

3. add four lines to xorg.conf.  here's what the section of xorg.conf looked like before adding the lines:

```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
        
EndSection   
``` 

and after

```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
        Option          "MaxTapTime" "0"
        Option         "TapButton1" "0"
        Option         "TapButton2" "0"
        Option         "TapButton3" "0"
EndSection
```

you can tell i'm a greenhorn. :biggrin:  steps one and two can be summed up with:  

sudo *yourtexteditor* /etc/X11/xorg.conf

---

### Post by sellyoursoulformusic on 2009-01-18
hmmmm.  maybe it's not the scroll area width that needs to be defined but the scroll area sensitivity.  is that possible?

---

