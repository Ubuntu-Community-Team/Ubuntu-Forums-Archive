---
title: "Why do my auto-hiding panels not hide (every time)?"
date: 2009-12-16
forum: New to Ubuntu
---

### Post by JamesParnell on 2009-12-16
Some times they do disappear, other times not. why is this??

---

### Post by wojox on 2009-12-17
Start gconf-editor ( Alt+F2 ) gconf-editor

Browse to /apps/panel/global

Set panel_hide_delay and panel_show_delay to more sensible (integer) values. Note that these values represent milliseconds!

---

### Post by audiomick on 2009-12-17
My panels are set to hide. Fairly often, the top panel stays open after selecting something until I click in it then back into the window of whatever I have running.

I haven't made a connection with any particular programme, although I can't exclude the possibility either.

I have no idea what causes it. I assume some problem or other with gnome itself or the desktop effects (that will hopefully get fixed one day).

edit: My machine is fairly fast (dual core cpu @ 3.3 GHz ) and has 4GB RAM, so it is unlikely to be a resources problem. I am using 64 bit 9.10. The problem has been there since 8.04.

---

### Post by W00ster on 2009-12-23
> **audiomick said:**
> My panels are set to hide. Fairly often, the top panel stays open after selecting something until I click in it then back into the window of whatever I have running.

I haven't made a connection with any particular programme, although I can't exclude the possibility either.

I have no idea what causes it. I assume some problem or other with gnome itself or the desktop effects (that will hopefully get fixed one day).

edit: My machine is fairly fast (dual core cpu @ 3.3 GHz ) and has 4GB RAM, so it is unlikely to be a resources problem. I am using 64 bit 9.10. The problem has been there since 8.04.

I have the same problem with autohide of panels in Gnome. The panels seems stuck when in fact it should be hiding.

Another issue with the panel, is if you take an application like Geeqie (image browser) into full screen mode, you are left with a line from the hidden panel, visible at the top and the bottom of the screen. Some times they disappear completely, other times they are visible.
By doing the same when running xfce or kde, the panels are completely hidden in full screen mode.

---

### Post by audiomick on 2009-12-23
> **W00ster said:**
> 
Another issue with the panel, is if you take an application like Geeqie (image browser) into full screen mode, you are left with a line from the hidden panel, visible at the top and the bottom of the screen. Some times they disappear completely, other times they are visible.
By doing the same when running xfce or kde, the panels are completely hidden in full screen mode.

I get that too. goes away if you re-maximize, I think.

---

