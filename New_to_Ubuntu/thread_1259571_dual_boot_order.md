---
title: "dual boot order"
date: 2009-09-06
forum: New to Ubuntu
---

### Post by ppb7 on 2009-09-06
After a few months working up to install jaunty (on dual boot), I can now enjoy what I call ¨sensible computing¨. However, I am conscious that the rest of the family may not be overjoyed by the move.
Among other things, as our computer is very slow to get going, it is usual to switch it on and log in then get on with doing something else (this is NOT the case with jaunty). So since I´&#7743; the only one using jaunty, I´d rather the operating system that booted automatically after a set time should be Windows.
How can I do that:?:

---

### Post by scragar on 2009-09-06
It might be worth profiling your boot first, see if that improves performance during boot any. At the grub menu press **e** on the ubuntu line, then **e** again on the line that starts kernel... at the end write the word **profile** press enter, then **b** to boot your modified line. This will take a while, but after this boot your normal boot should be a bit faster.

The default OS is set by a number in /boot/grub/menu.lst in the line that reads something like: "default 0"
```
sudo gedit /boot/grub/menu.lst
```
0 is the first OS on the list, 1 is second...

---

### Post by earthpigg on 2009-09-06
the program you want to install so you can point-and-click to change these settings is 'startup manager'.

it can be found in synaptic and in applications -> add/remove

dont go to crazy expeerimenting with startup manager or you may end up breaking GRUB.

good luck! :D

---

### Post by lindsay7 on 2009-09-06
+1 on installing "Startup Manager"  It is much easer to do then changing the menu.lst.  After installing it look in the System/Administration menu to find it.

---

