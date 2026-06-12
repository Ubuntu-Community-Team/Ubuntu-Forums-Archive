---
title: "how do i get the 3d rotating cube effect in ubuntu"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by kapi on 2009-01-31
wondered if anyone knows how to generate the roating 3d cube seen on many youtube videos of the ubuntu desk tops

Kapi

---

### Post by taurus on 2009-01-31
Maybe this is the one you're looking for.

[http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)

---

### Post by drs305 on 2009-01-31
Don't know which cube effect specificallty you are looking for. compiz is installed by default in intrepid. To install the compiz configuration settings manager to have full control over compiz settings:
```
sudo apt-get install compizconfig-settings-manager
```

Then System, Preferences, CompizConfig Settings Manager (or in terminal: ccsm). Desktop > Desktop Cube. There are other cube effects in this section as well. Just play with them to see which ones you like.

---

### Post by kapi on 2009-01-31
much appreciated - thankyou for your help

---

### Post by wolfen69 on 2009-01-31
Go to system>admin>hardware drivers. install your video card driver. Reboot. then open the terminal and
Code:

```
sudo apt-get install compizconfig-settings-manager
```

Then go to system>preferences>appearance>visual effects and enable "extra". Then go to system>preferences>advanced desktop effects settings to enable what effects you want.

Here is a list of some of the things you can do

Desktop Effects1 Keyboard Shortcuts
Rotate Cube Mousewheel on Desktop
Switcher2 Alt + Tab
Shift Switcher3 Super + Tab (2 modes: flip and cover)
Ring Switcher Super + Tab - overrides Shift Switcher
Expo Super + E (toggle)
Film Effect Ctrl + Alt + Down Arrow4
Rotate Cube Manually Ctrl + Alt + Left Mouse Button
Scale Windows Alt + Shift + Up Arrow
Show/Clear Desktop Ctrl + Alt + D (toggle)
Snapping Windows Move a window across workspaces5
Screenshot Super + Left Mouse Button
Zoom In/Out Super + Mousewheel
Transparent Window Alt + Mousewheel
Resize Window Alt + F8
Move Window Alt + F7
Add Helper Super + P
Widget Layer F9 (toggle)
Water Effects Shift + F9 (toggle)
Fire Effects: On Super + Shift + Left Mouse Button
Fire Effects: Clear Super + Shift + C
Annotate: Draw Super + Left Mouse Button
Annotate: Start Super + 1
Annotate: End Super + 3
Group: Select Window(s) Super + S
Group: Group Windows Super + T
Group: Ungroup Windows Super + U
Group: Flip Windows Super + Right or Left Arrow

Make sure the effects are enabled to see results. You can do so by going to System - Preferences - Advanced Desktop Effects Settings. Some effects will disable others. For example, the Desktop Wall will disable the Desktop Cube, Snapping Windows will disable Wobbly Windows and many more. Please let me know of more commands, so I can add more effects to the list.

---

### Post by kapi on 2009-06-09
talk about not ready my mail,

its a bit late but the effects listed here are fantastic!

just a reminder of why ubuntu is so brilliant

---

