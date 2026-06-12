---
title: "N-trig help"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by StarCucco on 2009-11-11
I am having some issues with Touchsmart TX2, i did all the things here
[http://ubuntuforums.org/showthread.php?t=1252492](http://ubuntuforums.org/showthread.php?t=1252492) It works but the stylus is like crazy it points like a few inches away from the pen tip, and with the touch too. And also wont left or right click. 

Running Ubuntu 9.10 64x  2.6.31-14-generic type?

---

### Post by Favux on 2009-11-11
Hi StarCucco,

Welcome to Ubuntu Forums!

It sounds like it isn't calibrated.  Can I see your xorg.conf?:
```
gedit /etc/X11/xorg.conf
```

Which windows version do you have installed?  Vista, Win7rc, or Win7.  I want to know the highest version you've installed even if you removed it so we know which version of the n-trig firmware you have.

---

### Post by StarCucco on 2009-11-11
I have Windows Vista & 7rc Installed. Current N-trig Firmware is Ver. 3.5.9.8.5, upgraded it for 7 then downgraded back for vista .

```
Section "ServerLayout"
    Identifier     "X.org Configured"
    InputDevice    "stylus"
    InputDevice    "touch"
EndSection

Section "InputDevice"
    Identifier  "touch"
    Driver      "wacom"
    Option        "Mode" "Absolute"
    Option        "Type" "touch"
    Option        "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse"
    Option        "MaxX" "9600"
    Option        "MaxY" "7200"
    Option        "ResX" "1280"
    Option        "ResY" "800"
    Option        "Touch" "on"
    Option        "USB" "on"
    Option        "TopX" "0"
    Option        "TopY" "0"
    Option        "BottomX" "9600"
    Option        "BottomY" "7200"
    Option        "Buttons" "5"
    Option        "Button1" "1"
    Option        "Button10" "1"
    Option      "Device"    "/dev/input/n-trig"
EndSection

Section "InputDevice"
    Identifier  "stylus"
    Driver      "wacom"
    Option        "Mode" "Absolute"
    Option        "Type" "stylus"
    Option        "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.1-event-mouse"
    Option        "MaxX" "9600"
    Option        "MaxY" "7200"
    Option        "ResX" "1280"
    Option        "ResY" "800"
    Option        "Button2" "3"
    Option        "USB" "on"
    Option      "Device"    "/dev/input/n-trig"
EndSection
```

---

### Post by Favux on 2009-11-11
Hi StarCucco,

By:
> upgraded it for 7 then downgraded back for vista
I assume you mean win7 rc?

OK, you have two different device inputs:
```
    Option        "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse"
and
    Option        "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.1-event-mouse"

```
They should be the same and the same one for your firmware, win7rc, as the HOW TO tells you.

But more than that you have the symlinks in too, which do the same thing.  You should have only one or the other.  I'm assuming this means you put the symlink rules in place.  So just substitute the symlink lines:
```
    Option      "Device"    "/dev/input/n-trig"

```
where the by-path lines are.  Comment out the by-path lines by putting "#" (without the quotes) in front of them.

I hope this is clear.

---

### Post by StarCucco on 2009-11-11
Thanks! It's works now! 
Another question though, is there pressure sensitivity?

---

### Post by Favux on 2009-11-11
Hi StarCucco,

Outstanding!  Nice job.  You're welcome.

There should be.  If you are using Gimp you need to configure the extended input devices.  See near the bottom of the [Wacom wiki]("https://help.ubuntu.com/community/Wacom").

---

