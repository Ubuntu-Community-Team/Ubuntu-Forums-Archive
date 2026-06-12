---
title: "restarting the display"
date: 2010-05-06
forum: New to Ubuntu
---

### Post by GrandVizier on 2010-05-06
every so often, when I start my computer, or wake it from hibernate, the display colors are way off - if I restart it or go to hibernate and back, the problem is fixed 

I imagine there must be some kind of command I can run from terminal to 'restart' the display? (would this be the same as restarting gnome?) 

obviously the other goal would be to fix the issue from ever happening, but I don't even know how to describe the issue let alone debug it

---

### Post by GrandVizier on 2010-05-06
note: I just learned of the 
CTRL+ALT+F3 
&
CTRL+ALT+F7
combos - switching back and forth the first time caused the colors to be off, and doing it again put things back to normal - so it looks like I found my easy fix

but if anyone has any insight or can help me figure out why this happens that would be great

---

### Post by Old *ix Geek on 2010-05-06
If you have it enabled, **[ctrl][alt][backspace]** restarts X, and that's much quicker than restarting the computer.

---

### Post by GrandVizier on 2010-05-16
I previously didn't have Ctrl+Alt+Backspace enabled

I now went into System->Preferences->Keyboard->Layouts and enabled the setting to 'Key sequence to kill the X server'
but nothing happens when I press this key combo??

and I'm still curious as to what underlying setup is causing this problem with my display

---

### Post by oldsoundguy on 2010-05-16
new kill all is now in effect.

right alt/print screen/k

this will restart without reboot.

---

