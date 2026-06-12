---
title: "Toughbook CF-T4 Touchscreen help?"
date: 2010-11-15
forum: New to Ubuntu
---

### Post by Cheesycrap on 2010-11-15
Okay, pretty big noob here.  Been going for like 2 hours now trying to figure out how to set up and calibrate my touch screen on my toughbook running ubuntu 10.10 .

So far all I've figured out I've got to edit /etc/X11/xorg.conf , but when I went to do that it wasn't there?  Little more research found out that it didnt exist, so I made it and made up this off of what some other guy put in a forum.

[INDENT]Section "InputDevice"
        Identifier      "Fujitsu TouchScreen"
        Driver          "evtouch"
        Option          "Device" "/dev/input/event6"
        Option          "DeviceName" "touchscreen"
        Option          "MinX" "230"
        Option          "MinY" "220"
        Option          "MaxX" "3900"
        Option          "MaxY" "3850"
        Option          "MoveLimit" "5"
        Option          "ReportingMode" "Raw"
        Option          "SendCoreEvents" "true"
        Option          "Emulate3Buttons" "true"
        Option          "Emulate3Timeout" "40"
        Option          "AutoServerLayout" "on"
EndSection[/INDENT]

And thats how the file sits at the moment.

In the system the "fujitsu takamisawa USB touch panel" is detected as a joystick, and finally, touching the touch screen sends the mouse cursor to the bottom right of the screen.

Thanks guys, any input is appreciated as nothings working yet!

---

### Post by Cheesycrap on 2010-12-27
Shamelessly bumping this... still in the same situation from a month ago, anyone out there?

---

### Post by Cheesycrap on 2011-04-26
many more months have passed.

I have become weak, my powers are fading, please can anyone help?

---

