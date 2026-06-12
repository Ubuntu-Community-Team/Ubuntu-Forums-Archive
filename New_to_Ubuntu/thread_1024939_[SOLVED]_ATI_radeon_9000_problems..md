---
title: "[SOLVED] ATI radeon 9000 problems."
date: 2008-12-29
forum: New to Ubuntu
---

### Post by the.scarecrow on 2008-12-29
I just installed Ubuntu 8.04 Hardy on a Dell Latitude D600 laptop. The only problems seem to relate to poor performance of the Graphics card. Some examples are Chess crashes in 3D mode, I cant play DVDs using MPlayer or Ogle or Movie Player (apps lockup) and GoogleEarth crashes as it is starting.

I carefully followed this HowTo [https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver") and it does not seemed to make much difference.

Before I changed anything my xorg.conf file looked like this:

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection
```

After following the HowTo xorg.conf looks like this:

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
        Identifier      "Radeon 9000"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-72
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Radeon 9000"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "1440x900"
        EndSubSection
EndSection

Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection
```

I see that when I enter "man radeon" into Terminal there are lots of options but I don't understand what to change to help my setup.

This may also be helpfull:
```
dell-d600:~$ glxinfo | grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Tungsten Graphics, Inc.

```

and this:
```
dell-d600:~$ glxinfo | grep "direct rendering"
direct rendering: Yes

```

I think this all looks OK but the 3D graphics don't seem to work. I'm stuck now and don't know what to try next, can anyone help please?

Regards

---

### Post by w4ett on 2008-12-29
Well, it looks as if you have the correct driver loaded, and the options correct.  I will recommend that you maximize the shared memory setting in your laptop's bios.

Another recommendation is that when running ANY 3D application (games), if you already have not done so, turn off ALL desktop effects and use metacity as your Window Manager.

BTW, I have a 9200 card, and could never get the 3D Chess to work properly.

---

### Post by the.scarecrow on 2008-12-29
> **w4ett said:**
> Well, it looks as if you have the correct driver loaded, and the options correct.  I will recommend that you maximize the shared memory setting in your laptop's bios.

Another recommendation is that when running ANY 3D application (games), if you already have not done so, turn off ALL desktop effects and use metacity as your Window Manager.

BTW, I have a 9200 card, and could never get the 3D Chess to work properly.

Thanks but there is no settings in the BIOS for shared memory, I use the Gnome desktop and do not want to change this and 3D chess does not look demanding, does it have bugs in 3D mode? In Win XP pro this same laptop seems to work fine, including the graphics card.

How else can I test 3D is working/not working apart from what I have already tried?

---

### Post by w4ett on 2008-12-29
> **the.scarecrow said:**
> Thanks but there is no settings in the BIOS for shared memory, I use the Gnome desktop and do not want to change this and 3D chess does not look demanding, does it have bugs in 3D mode? In Win XP pro this same laptop seems to work fine, including the graphics card.

How else can I test 3D is working/not working apart from what I have already tried?

Metacity is the standard Window Manager used in Gnome without the Desktop Effects enabled.  Go to System>Preferences>Appearance>Visual Effects and select "None"  This disables the Compiz Fusion, and it is normally required to disable it to run most games.

To see what your Frame Rendering rate is, in the terminal type:
```
glxgears
```
If you see the spinning gears, your 3D is working.

The main problem is that AMD/ATI proprietary driver does not support any cards earlier than the 9500 series with the current XServer.  What you are running is the community supported open source driver.

---

### Post by the.scarecrow on 2008-12-29
Oh right. The Visual Effects are set to None. I tried selecting Normal and after a short delay I get "Desktop effects could not be enabled"

Then I tried:
```
dell-d600:~$ glxgears
4532 frames in 5.0 seconds = 906.224 FPS
4529 frames in 5.0 seconds = 905.608 FPS
4525 frames in 5.0 seconds = 904.938 FPS
5711 frames in 5.0 seconds = 1142.186 FPS
5839 frames in 5.0 seconds = 1167.769 FPS
5839 frames in 5.0 seconds = 1167.647 FPS
5839 frames in 5.0 seconds = 1167.659 FPS
5839 frames in 5.0 seconds = 1167.622 FPS
5833 frames in 5.0 seconds = 1166.530 FPS
5839 frames in 5.0 seconds = 1167.718 FPS
5842 frames in 5.0 seconds = 1168.250 FPS
5838 frames in 5.0 seconds = 1167.577 FPS
5339 frames in 5.0 seconds = 1067.793 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 222286 requests (209502 known processed) with 0 events remaining.
```

The gears seem to work okay, the error was when I closed the gears window.

What do you think of that?

---

### Post by the.scarecrow on 2008-12-29
Update, I can play DVDs now. It seemed to be a problem only with encrypted DVDs so I re-installed libdvdcss.

The 3D ATI problems still exist though.

---

### Post by the.scarecrow on 2008-12-30
I still don't know what to try next, any suggestions are very welcome. GoogleEarth crashes while initialising and 3D chessboard disappears after each move, quit/restart displays the board again ready for my next move. I take this as a Graphics card setup problem.

---

### Post by the.scarecrow on 2008-12-30
After lots of reading and playing it seems that the ATI opensource drivers are working very well. The most complex 3D screensavers all run very smoothly. I could get GoogleEarth 4.2 to run using this in Terminal:

DISPLAY=:0 googleearth

but it only worked if I first deleted the .googleearth file automatically created in my home folder. Athough it worked fine, when I shut it down it saved loads of bug reports for no apparent reason. I couldn't prevent these bug reports so I deleted 4.2 then installed 4.3 to give the latest version a go.

That solved it, GoogleEarth 4.3 working perfectly so I'm delighted :D

I think I will now try to get Metacity working, I think I know how.

---

