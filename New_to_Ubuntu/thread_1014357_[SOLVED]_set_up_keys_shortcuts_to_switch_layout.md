---
title: "[SOLVED] set up keys shortcuts to switch layout"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by RomanIvanov on 2008-12-17
I installed Xubuntu 8.10 on my laptop Dell Vostro 1510.

I need to change switching of layout from default <Alt>+<Shift> to CapsLock.

In all forums advise to add this section to /etc/X11/xorg.conf
But no meter what I write here - ignored, even after restart.
```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us,ru"
        Option          "XkbVariant"    ",winkeys"
        Option          "XkbOptions"    "grp:switch,grp:caps_toggle,grp_led:scroll"
EndSection
```

Please help.

---

### Post by Shhnap on 2008-12-17
My advice would be to install compiz and edit your settings from there: you can change any key bindings you want via the compiz settings managed. However if you don't want compiz then maybe that is not for you.

---

### Post by RomanIvanov on 2008-12-18
Is there other ways? I pretty sure that that it is possible to done by changing configurations in the files.?

---

### Post by RomanIvanov on 2008-12-18
SOLVED: solution is here [http://ubuntuforums.org/showthread.php?t=1012669](http://ubuntuforums.org/showthread.php?t=1012669)

---

