---
title: "XFCE + Nautilus won't quit"
date: 2011-01-31
forum: New to Ubuntu
---

### Post by Dzvinka on 2011-01-31
How can I quit Nautilus? Supposedly it's Xubuntu ( with XFCE ); there are no panels, but right-clicking provides an Applications-Help-Reset-Exit-etc menu.  After some googling Nautilus taking over the desktop seems to be a common problem, and typing something like *killall nautilus* or *nautilus -q* in Terminal is recommended. How can I open Terminal with no right-click menu and no panels, and Alt+F2, which, as far as I've understood, opens the Terminal, doesn't work? Any other shortkeys?
Thanks in advance and sorry for a (probably) silly question =)

---

### Post by sisco311 on 2011-02-01
Hi and welcome to the forums!

You can press Ctrl+Alt+F1 to switch to a virtual console. Log in and run:
```
DISPLAY=:0.0 nautilus -q
```
and/or:
```
killall -9 nautilus
```
Then Ctrl+Alt+F7 (or [noparse]F8)[/noparse] to switch back to the GUI session.

---

