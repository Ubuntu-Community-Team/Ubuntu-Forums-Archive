---
title: "lost desktop menu bar?"
date: 2009-05-23
forum: New to Ubuntu
---

### Post by garyed on 2009-05-23
I set up a computer for my wife with xubuntu-hardy used mainly for internet.
She's new to computers & gets lost real easy but everything was working fine till today. Whatever she did there's no menu bar to click for programs or even to shutdown or change user. The icons are still on the desktop & they work. If I open a program & minimize it, it gets lost in never never land so I think her desktop setup got messed up but I don't know how to get back to the default setup. That would probably be fine. I could always put the icons back if anyone could help me get back to default setup.
thanks

---

### Post by john.nicholls on 2009-05-24
The main components you need are xfwm4 (window manager), xfce4-panel (panel), and xfdesktop (background). If you've lost the panel, as appears to be the case, open the run dialog (alt-F2) and run xfce4-panel (you can do the same with the other two if necessary).

When everything is set up to your satisfaction, go to the Xfce4 Settings Manager, Session and Startup, and make sure Automatically save session on output is selected. If you want to save your session at any other time, right-click on a blank part of the panel, and select Restart.

---

### Post by garyed on 2009-05-24
Thanks John,

That worked perfectly.

---

