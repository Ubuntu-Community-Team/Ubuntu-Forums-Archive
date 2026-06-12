---
title: "missing a menu bar"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by wkuace on 2008-12-31
I'm running ubutu 8.10 in wubi. i installed the ati video driver using a thread i found that gave me a terminal command to install it. The video looks great now (had static) but i've lost the bar at the bottom of the screen that shows the 2 desktops, trash can, the minimized windows,etc. Is there a terminal command or option that would let me turn it back on or find if its on and just outside the window? i can still change desktops by scrolling with my mouse.

---

### Post by Michael.Godawski on 2008-12-31
hi, 

perhaps you can create a new bottom panel. Right click onto the existing one and select 
New Panel. Then right click onto it and select Add to Panel. Add what you need.

---

### Post by abn91c on 2008-12-31
right click on the remaining bar select the option to add another one. you will need to add the other items manually also

---

### Post by wkuace on 2008-12-31
there is no bar at all just a blank space. firefox will open up and leave space for it like when it was there. when i right click where it should be i just get the same options as clicking anywhere on the desktop.

---

### Post by phantomjoker on 2008-12-31
right click on the REMAINING menu bar (the one at the top) and select new panel

---

### Post by Michael.Godawski on 2008-12-31
[http://godawski.oxyhost.com/gnomepanel.html](http://godawski.oxyhost.com/gnomepanel.html)
 Try this to bring them back:
 
[LIST]
[*]Press Alt+F2, you will get "Run" dialog box.
[*]Type ```
gnome-terminal
```
[*]In terminal window, run ```
killall gnome-panel
```
[*]Wait for a moment, you should get gnome panels.
[/LIST]
 If alt+f2 does not work change with ctrl+alt+f1 into the command line gui. You will have to type in your login name and the login password. The password will not be displayed as you type it.
 Now you can run ```
killall gnome-panel
```.
 To leave the command line interface type ```
exit
``` and hit enter.

---

### Post by wkuace on 2008-12-31
sorry I didn't understand i'm a dork lol. the new panel worked. :) Thank you.

---

