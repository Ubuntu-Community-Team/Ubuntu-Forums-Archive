---
title: "Bamboo one in ubunt 10.04.1"
date: 2010-10-26
forum: New to Ubuntu
---

### Post by juzzy on 2010-10-26
Wondering if anyone can help? I am trying to get the bamboo one ctf-430 tablet to work with ubuntu 10.04.1.  It kinda works but the cursor is jumping to the point of contact on the pad, whereas, I need it to act the same as a laptop mousepad, where the cursor stays put when you raise the pen and begins again at the same point regardless of where the pen is on the pad.  I assume this is just an "options" issue but not sure how to change it??

would appreciate any help thanks.

---

### Post by Favux on 2010-10-26
Hi juzzy,

You have the Mode set to Absolute and you want Relative.  You can use an xsetwacom command or add an Option to the usb snippet in 10-wacom.conf.  That would look like:
```
Section "InputClass"
	Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#	MatchProduct "Wacom|WALTOP|WACOM"
	MatchProduct "Wacom|WACOM"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
	Option "Mode" "Relative"
EndSection
```
And to edit the wacom.conf file use:
```
gksudo gedit /usr/lib/X11/xorg.conf.d/10-wacom.conf
```

---

### Post by juzzy on 2010-10-26
As simple as that!!! That worked a treat, thank you very much for your help.

---

