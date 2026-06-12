---
title: "how to delay clicks/debounce a mouse button?"
date: 2011-06-03
forum: New to Ubuntu
---

### Post by outleradam on 2011-06-03
[LEFT]My mouse button seems to be a bit sensitive.  Sometimes it double clicks or tripple clicks when I click once.  Is there a way to make the mouse not react for 1ms or something so I don't get double clicks when I intend to get a single click?
[/LEFT]

---

### Post by JohnBonne on 2011-06-03
Snsitivity and other mouse adjustments are available in the Control center. There are two places where a mouse can be tuned up in there.

Type "gnome-control-center" (without the quotes) into  terminal (Alt+f2)

BTW: I can't get my mouse to single-click either.

---

### Post by outleradam on 2011-06-03
I found the "Control Center">"Mouse Preferences"> "Double-Click Timeout"....  It did not work even on the longest setting. Anything else I can try?  

here is my mouse from the /etc/X11/xorg.conf
```
Section "InputDevice"
    Identifier     "MX Rev"
    Driver         "evdev"
    Option         "Device" "/dev/input/event3"
    Option         "CorePointer"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "HWheelRelativeAxisButtons" "7 6"
    Option         "Buttons" "19"

```
This issue is very annoying.

---

### Post by JohnBonne on 2011-06-03
> **outleradam said:**
> I found the "Control Center">"Mouse Preferences"> "Double-Click Timeout"....  It did not work even on the longest setting. Anything else I can try?  


[/code]This issue is very annoying.

Sorry for the annoyance, :(. Have you tried reinstalling the mouse software. I am new at this, but last resort is reinstalling software and not trying to rewrite script. I am a first-time user running Nattty on a laptop.

---

### Post by outleradam on 2011-06-03
There is no mouse software.  When I click, it clicks twice or three times.

---

### Post by outleradam on 2011-06-03
I want a delay for 1 click to the next.  I need it to not read an extremely quick double click or tripple click.

---

### Post by JohnBonne on 2011-06-03
> **outleradam said:**
> There is no mouse software.  When I click, it clicks twice or three times.

Install **btnx** or **pointing devices**.

[http://ubuntuforums.org/showthread.php?t=455656](http://ubuntuforums.org/showthread.php?t=455656)

---

