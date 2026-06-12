---
title: "KeyboaRD mAfuntion"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by Lyrmese on 2009-08-12
Hello! I've been using Ubuntu for several months now, but I still consider myself a newb. There's so much about Linux and OSes in general that I want to learn.

Enough about that, though; I need some help! Last week, my keyboard began acting strangely.


[LIST]
[*]Whenever I press the 'A' key, Caps Lock would activate, in addition to printing the letter 'a' OR 'A' on the screen. The same thing happens when I press the Caps Lock key.
[*]Whenever I press the 'Q' key, ',q' is printed on the screen.
[*]Whenever I press the 'Z' key, '+z' is printed on the screen.
[/LIST]

It's very annoying, especially when typing in passwords. Can someone help me figure out what's wrong? Is it an Ubuntu problem, a GNOME problem, or neither?

Lyrmese

---

### Post by jmac0101 on 2009-08-12
Have you tried a new keyboard? Maybe it's hardware.

---

### Post by desperado665 on 2009-08-12
> **jmac0101 said:**
> Have you tried a new keyboard? Maybe it's hardware.


+1

sounds like hardware. If it's a desktop, also check connector for bent pins.

---

### Post by Lyrmese on 2009-08-12
A hardware problem? I have no way of knowing without buying a new one, so I guess that's all I can do.

Thanks.

---

### Post by niteshifter on 2009-08-12
Hi,

Well we can do this before spending $$$$ on a keyboard:

In Terminal type:
```
xev
```
This will start the X event viewer. X pretty much deals with all human interaction with the system, not just video / graphics.
Ignore what xev produces when it first starts up. Also try to avoid moving the mouse over xev's window - it will "see" that an produce output in the Terminal, we're just reducing clutter in the output by doing this.

Press the problem keys and look at the output in the Terminal window. Below is mine for keys q,z and a:
```
KeyPress event, serial 31, synthetic NO, window 0x5400001,
    root 0x13b, subw 0x0, time 2897805, (171,-18), root:(1004,35),
    state 0x0, keycode 24 (keysym 0x71, q), same_screen YES,
    XLookupString gives 1 bytes: (71) "q"
    XmbLookupString gives 1 bytes: (71) "q"
    XFilterEvent returns: False

KeyRelease event, serial 31, synthetic NO, window 0x5400001,
    root 0x13b, subw 0x0, time 2897922, (171,-18), root:(1004,35),
    state 0x0, keycode 24 (keysym 0x71, q), same_screen YES,
    XLookupString gives 1 bytes: (71) "q"
    XFilterEvent returns: False

KeyPress event, serial 31, synthetic NO, window 0x5400001,
    root 0x13b, subw 0x0, time 2899023, (171,-18), root:(1004,35),
    state 0x0, keycode 52 (keysym 0x7a, z), same_screen YES,
    XLookupString gives 1 bytes: (7a) "z"
    XmbLookupString gives 1 bytes: (7a) "z"
    XFilterEvent returns: False

KeyRelease event, serial 31, synthetic NO, window 0x5400001,
    root 0x13b, subw 0x0, time 2899138, (171,-18), root:(1004,35),
    state 0x0, keycode 52 (keysym 0x7a, z), same_screen YES,
    XLookupString gives 1 bytes: (7a) "z"
    XFilterEvent returns: False

KeyPress event, serial 31, synthetic NO, window 0x5400001,
    root 0x13b, subw 0x0, time 2900335, (171,-18), root:(1004,35),
[B]    state 0x0, keycode 38 (keysym 0x61, a), same_screen YES,
    XLookupString gives 1 bytes: (61) "a"
    XmbLookupString gives 1 bytes: (61) "a"
    XFilterEvent returns: False
[/B]
KeyRelease event, serial 31, synthetic NO, window 0x5400001,
    root 0x13b, subw 0x0, time 2900445, (171,-18), root:(1004,35),
[B]    state 0x0, keycode 38 (keysym 0x61, a), same_screen YES,
    XLookupString gives 1 bytes: (61) "a"
    XFilterEvent returns: False
[/B]
```
What's of interest in the output I bold-faced for the "A" key press. Yes, there are two events: First is for key pressed, the next is key released.

Does yours look similar or is it different?

---

