---
title: "TouchPad Scrolling One-Way Only"
date: 2010-12-17
forum: New to Ubuntu
---

### Post by KlytusLord on 2010-12-17
Greetings all,

I just installed Ubuntu:
Release 10.10
Kernel 2.6.35-23 generic
Gnome 2.32.0

My Computer is an Acer Aspire 2551.

I had trouble getting the WiFi card to work, but I eventually found the solution here in the forums.

Now, there is one small problem remaining.

My touchpad only scrolls in one direction: down.
When I try to scroll up, what happens is that the document in question scrolls all the way down to the end. The equivalent of pressing Ctrl-End.

I don't care about any advanced features on the touchpad, and normal cursors movement is fine, so if I can fix the scroll up issue, I'll be set.

In my Mouse settings (System/Preferences/Mouse) there is no tab for scrolling at all. I only have the General and Accessibility tabs, so I am guessing the OS is not detecting the touchpad properly.

Thanks for any help with this, and Happy Holiday Season!

---

### Post by KlytusLord on 2010-12-18
I have had no luck solving this issue:

I added the following to my xorg.conf file:

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "SHMConfig"             "on"
        Option          "HorizScrollDelta"      "0"
	Option		"VertScrollDelta"	"0"
EndSection

I was hoping to at least disable scrolling altogether, but it had no effect at all. Scrolling is still on, and it only works in the down direction.

Sensitivity on the touchpad is also very bad, moving is ok, but tapping is all over the place in terms of how hard I have to tap for it to register.

my xinput list does not have the touchpad listed. it lists a generic PS/2 wheel mouse, which is I am guessing the problem is rooted, the fact that Ubuntu does not see my touchpad.

Thanks for any help.

---

