---
title: "Menu bar alterations"
date: 2011-03-21
forum: New to Ubuntu
---

### Post by Canime on 2011-03-21
This could be seen as picky, but its a new system and I want everything to look perfect. The menu bar when I change the opacity or system color in, right-click panel -> properties, background tab, any of the options there change only the background of the middle bar, rather than the buttons, menu-options and the rest of it, see image. Is there a tool that allows you to alter the menu bar specifically to get it all one color and not various colors?

---

### Post by ashmew2 on 2011-03-22
Hi , im not really a fan of eye candy , but i do respect you wanting the system to be *PERFECT* as u want ....

Maybe this could get u started : [http://askubuntu.com/questions/7561/how-to-change-the-color-of-menu-text](http://askubuntu.com/questions/7561/how-to-change-the-color-of-menu-text)
GTK Theming looks promising , check out the link at the bottom.

I'll look around and post back if i find anything more useful.

---

### Post by mcduck on 2011-03-22
Your problem is that the GTK theme you are using is defining a specific color (or background image) for panel applets. That will override whatever you try to configure yourself.

Luckily, the solution is fairly simple. You just need to remove such definitions from the GTK theme, and usually there's a separate "panel.rc" (or similar) file which you can just rename/delete to remove panel theming from the GTK theme.

---

