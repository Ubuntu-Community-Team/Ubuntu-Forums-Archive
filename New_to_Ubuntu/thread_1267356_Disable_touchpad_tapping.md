---
title: "Disable touchpad tapping?"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by del_diablo on 2009-09-15
Currently sitting with xterm up here and reading on xinput list-props 6 and man synaptics.
Gsynaptics and qsynaptics along with ksynaptics wants some line enabled in xorg.conf, which i have seen cases reported on that it does not work. And frankly, the last times i have messed with my xorg.conf i always ended up killing the graphics until it was reconfigured automaticly with the tools my propitary driver provided.

```
delly@delly-laptop:~$ xinput list-props 6
Device 'SynPS/2 Synaptics TouchPad':
	Device Enabled (99):		1
	Synaptics Edges (246):		1632, 5312, 1575, 4281
	Synaptics Finger (247):		24, 29, 255
	Synaptics Tap Time (248):		180
	Synaptics Tap Move (249):		221
	Synaptics Tap Durations (250):		180, 180, 100
	Synaptics Tap FastTap (251):		0
	Synaptics Middle Button Timeout (252):		75
	Synaptics Two-Finger Pressure (253):		280
	Synaptics Scrolling Distance (254):		100, 100
	Synaptics Edge Scrolling (255):		1, 0, 0
	Synaptics Two-Finger Scrolling (256):		0, 0
	Synaptics Edge Motion Pressure (257):		29, 159
	Synaptics Edge Motion Speed (258):		1, 401
	Synaptics Edge Motion Always (259):		0
	Synaptics Button Scrolling (260):		1, 1
	Synaptics Button Scrolling Repeat (261):		1, 1
	Synaptics Button Scrolling Time (262):		100
	Synaptics Off (263):		0
	Synaptics Guestmouse Off (264):		0
	Synaptics Locked Drags (265):		0
	Synaptics Locked Drags Timeout (266):		5000
	Synaptics Tap Action (267):		2, 3, 0, 0, 1, 2, 3
	Synaptics Click Action (268):		1, 1, 1
	Synaptics Circular Scrolling (269):		0
	Synaptics Circular Scrolling Trigger (270):		0
	Synaptics Circular Pad (271):		0
	Synaptics Palm Detection (272):		0
	Synaptics Palm Dimensions (273):		10, 199
	Synaptics Pressure Motion (274):		29, 159
	Synaptics Grab Event Device (275):		1
```

So what command do i need to input to disable tapping for good?

---

### Post by neurostu on 2009-09-15
If I remember correctly the gsynaptics package will let you configure the touchpad and disable it.

---

### Post by Darkwing-Duck on 2009-09-15
Give this Wiki page a shot. Maybe you can find your help in there!
 
[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)
 
Hope it helps

---

### Post by del_diablo on 2009-09-16
> **neurostu said:**
> If I remember correctly the gsynaptics package will let you configure the touchpad and disable it.

Please at the least bother to read the post?
Like this lines:
> **del_diablo said:**
> Gsynaptics and qsynaptics along with ksynaptics wants some line enabled in xorg.conf, which i have seen cases reported on that it does not work. And frankly, the last times i have messed with my xorg.conf i always ended up killing the graphics until it was reconfigured automaticly with the tools my propitary driver provided.

Wonderly: thanks for the link, sadly there is no relevant information there :(. Everything involves editing xorg.conf or disabeling scrolling AND tappiing or turning it off, or to use g/k/qsynaptics :(

---

### Post by vanadium on 2009-09-16
Seems that in the next Ubuntu version, it will be disabled by default, but there will be an option in the gui to turn it on.

I also work without touchpad. You indeed currently need to install gsynaptics, then add the line "    Option	   "SHMConfig" "on"
" to the Inputdevice section before you can use the config tool, but anyhow I do not see why this procedure does not work for you.

---

### Post by del_diablo on 2009-09-16
> 
X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux delly-laptop 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Sep 16 17:39:01 2009
(==) Using config file: "/etc/X11/xorg.conf"
Parse error on line 60 of section InputDevice in file /etc/X11/xorg.conf
	This section must have an Identifier line.
(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

(WW) xf86CloseConsole: KDSETMODE failed: Bad file descriptor
(WW) xf86CloseConsole: VT_GETMODE failed: Bad file descriptor
(WW) xf86OpenConsole: VT_GETSTATE failed: Bad file descriptor
 ddxSigGiveUp: Closing log


This happens when i modify my xorg.conf
I added this:
```
Section "InputDevice"
Option "SHMConfig" "on"
EndSection
```

Which you said i should.
*sigh* this is why i refused to add the line, it ALWAYS crash when i modify it the slightest :(

---

### Post by Maheriano on 2009-09-16
Can't you just check the box in the mouse options?

---

### Post by wojox on 2009-09-16
You don't put it in xorg.conf.

Open:

```
gksudo gedit /etc/hal/fdi/policy/shmconfig.fdi
```

Add:

```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <match key="input.x11_driver" string="synaptics">
      <merge key="input.x11_options.SHMConfig" type="string">True</merge>
    </match>
  </device>
</deviceinfo>
```

Save and close that file, reboot, and SHMConfig should be enabled. 


[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

---

### Post by ladybehemot on 2009-09-17
Is there a reason why you don't want to do it with System>Preferences>mouse>touchpad ?

---

### Post by del_diablo on 2009-09-17
> **ladybehemot said:**
> Is there a reason why you don't want to do it with System>Preferences>mouse>touchpad ?

READ THE TREAD! wojox last post solved the pussle, and no i do not run GNOME! And the config in GNOME required the line i added to a certain config as pointed out by wojox, so it was useless.

wojox: Thanks it did the trick, it enabled gsynaptics to do the trick :P

---

