---
title: "How to relaunch the panel at the top of the desktop?"
date: 2011-04-17
forum: New to Ubuntu
---

### Post by aaron76 on 2011-04-17
Like an idiot, I deleted the control panel at the top of the screen.
Now, I can't find a way to open the software centre etc, along with a lot of other useful things.
The solution is probably very simple, but right now I'm stuck.
Any help would be appreciated.
Thanks.

---

### Post by el_koraco on 2011-04-17
Do you mean the menu? Right click on panel, add to panel, there's options like custom menu, menu, and something else. Or if you deleted the panel itself, right click on desktop, add panel, then start adding things to it.

---

### Post by Frogs Hair on 2011-04-17
Try alt+F2 , type gnome-terminal and select run . Copy & paste this into the terminal and press enter.
```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

---

### Post by aaron76 on 2011-04-17
Thanks for the quick replies. I managed to fix it myself.
It was indeed the entire panel.

---

### Post by dcsoldschool53 on 2011-04-17
> **aaron76 said:**
> Thanks for the quick replies. I managed to fix it myself.
It was indeed the entire panel.

If you fix it, mark this thread as solved.

---

