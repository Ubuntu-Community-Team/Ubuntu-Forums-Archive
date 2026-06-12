---
title: "Trapped in Right Screen of Dual Monitor"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by pmains on 2008-12-18
I posted earlier about my Dual Monitor Setup ([ http://ubuntuforums.org/showthread.php?t=1008378 ]("http://ubuntuforums.org/showthread.php?t=1008378")) and have found some success. I can now see both monitors, but once I go from the right monitor to the left, my mouse is trapped on the right side.

Also, the monitors occasionally dim, before lighting up again. Very strange.

Not to mention, the dual monitor only began to work after I rebooted completely. Simply restarting the GDM is not effective, as I end up without any input whatsoever -- even after hitting ctrl-alt-F5/F6.

So, here is my current "Layout"

Section "ServerLayout"
    Identifier  "Default Layout"
    screen 0 "Default Screen" LeftOf "Right Screen"
    screen 1 "Right Screen"
    Inputdevice "Generic Keyboard"
    Inputdevice "Configured Mouse"
EndSection
Section "Module"

Using RightOf with Screen 1 instead of LeftOf with Screen 2 doesn't make a difference. Adding 0 0 after Screen 0 (while using RightOf rather than LeftOf) doesn't make a difference. I'm not sure what I'm doing wrong, or what to do next.

---

