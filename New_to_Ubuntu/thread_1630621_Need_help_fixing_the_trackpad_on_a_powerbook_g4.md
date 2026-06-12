---
title: "Need help fixing the trackpad on a powerbook g4"
date: 2010-11-25
forum: New to Ubuntu
---

### Post by cpu_medic on 2010-11-25
Hi guys, ok here's my problem, I have just installed ubuntu 10.10 on my old powerbook g4. everything kinda works, however, the trackpad only seems to let me move the mouse up, and down. it will not move left to right. i have done research, and came up with the appletouch driver. this is where i hit a wall. i can't figure out how to compile the driver, and when (if) i figure out how to compile it, how do i install it?

---

### Post by khelben1979 on 2010-11-25
**modprobe appletouch** loads the driver from the Linux kernel. [Apple Touchpad Driver]("http://www.popies.net/atp/index.html") (appletouch) describes a bit how it looks like, including instructions. Hope it helps!

---

### Post by KiLaHuRtZ on 2010-11-27
I also **was** plagued by this issue.  I just got done installing Maverick on my iBook G4 about 1.5 hours ago and have been messing with this since.

I am happy to report that I crafted a possible workaround after "Google'ing" around a bit.

I took the settings from the kernel module (appletouch) maintainer [_here_]("http://www.popies.net/atp/index.html") and setup X to use them.

It's not 100% but it's a 95% improvement versus what it was.

This is what I did.

```
sudo mv /usr/share/X11/xorg.conf.d /usr/share/X11/xorg.conf.d.bak

sudo mkdir /usr/share/X11/xorg.conf.d

sudo cp /usr/share/X11/xorg.conf.d.bak/10-evdev.conf /usr/share/X11/xorg.conf.d/.

sudo vi /usr/share/X11/xorg.conf.d/50-appletouch.conf
```

Add the config to this file and save; or download it from me [_here_]("http://www.digitalenigma.net/~luke/ubuntu/maverick/appletouch-fix/50-appletouch.conf").

```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"auto-dev"
	Option		"LeftEdge"		"0"
	Option		"RightEdge"		"850"
	Option		"TopEdge"		"0"
	Option		"BottomEdge"		"645"
	Option		"MinSpeed"		"0.4"
	Option		"MaxSpeed"		"1"
	Option		"AccelFactor"		"0.02"
	Option		"FingerLow"		"55"
	Option		"FingerHigh"		"60"
	Option		"MaxTapMove"		"20"
	Option		"MaxTapTime"		"100"
	Option		"HorizScrollDelta"	"0"
	Option		"VertScrollDelta"	"30"
	Option		"SHMConfig"		"on"
EndSection
```

Now you should have a file tree like this.

```
/usr/share/X11/xorg.conf.d
&#9500;&#9472;&#9472; 10-evdev.conf
&#9492;&#9472;&#9472; 50-appletouch.conf
/usr/share/X11/xorg.conf.d.bak
&#9500;&#9472;&#9472; 10-evdev.conf
&#9500;&#9472;&#9472; 50-synaptics.conf
&#9500;&#9472;&#9472; 50-wacom.conf
&#9500;&#9472;&#9472; 51-synaptics-quirks.conf
&#9492;&#9472;&#9472; 60-magictrackpad.conf
```

Now restart GDM.

```
sudo /etc/init.d/gdm restart
```

And change your mouse settings like this; or whatever works best for you.

[IMG]http://www.digitalenigma.net/~luke/ubuntu/maverick/appletouch-fix/mouse-settings.png[/IMG]

Hope this helps you guys out...

Oh, and make sure you are using kernel train version 2.6.35-[COLOR="Red"]23[/COLOR]...

---

