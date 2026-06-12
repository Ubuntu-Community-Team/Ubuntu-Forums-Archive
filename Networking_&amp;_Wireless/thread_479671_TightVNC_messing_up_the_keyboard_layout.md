---
title: "TightVNC messing up the keyboard layout"
date: 2007-06-20
forum: Networking &amp; Wireless
---

### Post by dushkin on 2007-06-20
Hi.

I've been fighting with this problem for a while now - I have a Feisty server box running TightVNC (latest in stable). I try connecting with different clients and every time I get the same problem: the keyboard layout is messed up.

When it asked me during the setup which keyboard layout I want I said Dvorak, so it might be trying to hardwire the keyboard or something but when it receives raw input or something it freaks out and fails.

This problem in theory could happen in all foreign layouts. 

Is there some way to set the layout back to QWERTY without reinstalling or something to try and solve this?

Thanks

---

### Post by abhi.datt on 2008-04-23
This is a documented bug and the solution is run the following command from the user shell who needs to access the desktop from vnc

gconftool --set /desktop/gnome/peripherals/keyboard/kbd/layouts --type List --list-type String [aa]

---

