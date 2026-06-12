---
title: "unity wacom touchstrip"
date: 2011-07-31
forum: New to Ubuntu
---

### Post by hamishmacd on 2011-07-31
I have a Wacom Intuos 3. Its touch strips (which I never use) activates Unity to appear every time my hand hovers anywhere near them. I've seen posts by people who want to enable their touch strips, none by those who want to disable them. Does anyone know of any way to stop this happening? Every time I move my cursor anywhere near the top LHS of the screen I end up clicking my Home folder rather than say the back button of Firefox.

The contents of my /usr/share/X11/xorg.conf.d/50-wacom.conf file are as follows

Section "InputClass"
    Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#    MatchProduct "Wacom|WALTOP|WACOM"
    MatchProduct "Wacom|WACOM|Hanwang"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
    Option "Button1" "1"
    Option "Button2" "3"
    Option "Button3" "2"
EndSection

Section "InputClass"
    Identifier "Wacom serial class"
    MatchProduct "Serial Wacom Tablet"
    Driver "wacom"
EndSection

Section "InputClass"
        Identifier "Wacom serial class identifiers"
        MatchProduct "WACf|FUJ02e5|FUJ02e7"
        Driver "wacom"
EndSection


# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
    Identifier "Wacom N-Trig class"
    MatchProduct "HID 1b96:0001|N-Trig Pen"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
    
EndSection

---

