---
title: "Can not disable touchpad"
date: 2010-06-26
forum: New to Ubuntu
---

### Post by eyeofreason on 2010-06-26
Using Linux Mint 8. I am trying to disable the touchpad and use only my wireless mouse.  I've tried gsynaptics and gpointing-device-settings. They both will disable the touchpad for about 2 minutes and then it starts moving again. When I open the gui it's as if i'd never made changes. 

If anyone can help, thank you!

---

### Post by limpdisk on 2010-06-26
Open GUI Configuration Editor -- (Hold down 'Alt' key, press 'F2' key).  Type 'gconf-editor' (without quotes) in window, click 'Run'.

In GUI edit window open  > desktop (click '>' icon), do same > gnome > peripherals, click on  'touchpad'.  
In the window on right, uncheck "touchpad_enabled" box.

Close

---

### Post by eyeofreason on 2010-06-26
Wow cool thanks for that. It's nice to know. I ticked the off box under the touchpad tab. It didn't work, but I'm glad i know how to find these options.

---

### Post by limpdisk on 2010-06-26
In the touchpad edit window is the single 'off' line.  Leave checked.  several lines farther down is the touchpad_enabled line.  Uncheck that.

---

### Post by corncob on 2010-06-26
At the top of my Gateway NV54 keyboard there are what have been called fx86 keys.  They raise, lower or mute sound, turn wifi on or off, etc.  There is also a key to turn the touchpad off.  It looks like a touchpad with a finger on it and an "X" on the hand.  When lit the touchpad is off.  I have to press this every time I turn the computer on if I want to disable the touchpad.

---

### Post by valley1967 on 2010-06-26
Thank you very much have been going nuts with this:lolflag:

---

### Post by eyeofreason on 2010-06-27
under the "off" box i have," tap _to_click". That's the only box below "off".That's in Karmic or Helena (mint 8)

---

