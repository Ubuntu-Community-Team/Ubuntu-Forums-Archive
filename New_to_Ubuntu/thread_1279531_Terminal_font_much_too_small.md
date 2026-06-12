---
title: "Terminal font much too small"
date: 2009-09-30
forum: New to Ubuntu
---

### Post by dave WB3DWE on 2009-09-30
[SIZE=3][FONT=Lucida Sans Unicode]As it comes up the terminal font is about size 6, much too small for me to read. Bringing the window up to full size does not enlarge the font. Its View submenu says to enlarge with Ctrl & + (it uses somewhat ambiguous Ctrl++). Many times I've tried with the + key on numeric keypad and failed. The keypad is turned on. Then I discovered it could be done with Ctrl & a shifted =\+ key on the keyboard. Is this wierdness cubed ?
    1. is there any way to put a "switch" on terminal so it comes
  up with a larger font ?
    2. Any explanation why the keyboard =+ key works but not the + key on numeric keypad ?
I'm using Ubuntu 9.04     Thanks.

[/FONT][/SIZE]

---

### Post by BQAggie2006 on 2009-09-30
Try this - open a terminal, click Edit >> Profiles. Under the General tab, un-check the "Use the system fixed width font" box, then click the font, and change to the font and size you would prefer. Click Close when finished. The terminal now should now come up everytime using that font.

---

### Post by doas777 on 2009-09-30
you can also zoom and out on terminals, under teh view menu. I think that is a per session thing though.

---

### Post by dearingj on 2009-09-30
There are two ways you can fix this problem:

1) Change your system's fixed-width font size. Open System->Preferences->Appearance, click the Fonts tab, and adjust the setting for fixed-width font.

2) Set the terminal to ignore the system's fixed-width font size and instead use its own setting. In a terminal window, click Edit->Profile Preferences. Then on the general tab, uncheck "Use the system fixed width font", then change the font setting there.

Edit: I see somebody beat me to the punch :)
I'd still recommend changing your system's font setting, as the terminal isn't necessarily the only program that will use it.

---

### Post by dave WB3DWE on 2009-10-01
[SIZE=3][FONT=Lucida Sans Unicode]Thanks to all for the solutions.      Dave, an "adoptive" TX aggie
( sons, daughter-in-law, faculty and a late friend who was        middle linebacker )
[/FONT][/SIZE]

---

