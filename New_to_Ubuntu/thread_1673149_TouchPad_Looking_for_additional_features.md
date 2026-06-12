---
title: "TouchPad: Looking for additional features"
date: 2011-01-22
forum: New to Ubuntu
---

### Post by KlytusLord on 2011-01-22
Hello all,

I can't seem to find any information on these two features for touchpads.

1. Tap-Drag lock, meaning I can tap once to select, move the item around even by removing my finger from the touchpad, and then releasing by clicking again.

2. Snap to default button; when a dialog or popup appears, the cursors automatically goes to the default choice.

All of the extra information I have found so far deals with multitouch options and completely disabling the pad.

This is on a Vostro 3500, which has a Synaptics pad. Any tools or command-line options to get these features in Ubuntu?

Thanks!

---

### Post by KlytusLord on 2011-01-25
I have tried the following in my xorg.conf file ...

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizScrollDelta"      "0"
	Option		"LockedDrags"		"true"
EndSection

However, it is not making any difference is the drag lock feature.

I had to create the file itself, since it did not exist. I am not sure if that makes any difference; maybe I am missing something that all xorg.conf files must have?

---

