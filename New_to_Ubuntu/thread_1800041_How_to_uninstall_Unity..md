---
title: "How to uninstall Unity."
date: 2011-07-08
forum: New to Ubuntu
---

### Post by parkerskouson on 2011-07-08
I just switched to Natty. But i hate Unity. Is there any way to uninstall Unity or just remove it from the desktop? 

Thanks

Parker

---

### Post by IWantFroyo on 2011-07-08
Log out, and look for a pull-down bar that says "Ubuntu" at the bottom.

Click on it, and select Ubuntu classic. You can remove Unity, but it might pull some stuff out of Ubuntu Classic as well (themes? wallpapers?).

---

### Post by parkerskouson on 2011-07-08
Perfect. Would u be willing to answer 2 more things?

---

### Post by IWantFroyo on 2011-07-08
Sure. What are they?

PS- You can find Unity in the Software Center and Synaptic, although I would advise you tread with caution.

---

### Post by parkerskouson on 2011-07-08
Is there any way to remove the bottom bar off of ubuntu classic(the one with trash and desktop shortcut). And also is there any other program to creat desktop shortcuts with?

---

### Post by srisharan on 2011-07-08
To remove the bottom gnome panel, just right click on it and click on the delete this panel option.Now to remove after the top one has also been deleted,yes there is a way but it will remove useful shortcuts like alt+F2.A better method is to open gconf-editor(alt+F2 or terminal)and got o apps>panel>levels>your_panel and autohide it and set the unhide delay to a big no(like 999999)

---

### Post by srisharan on 2011-07-08
To create desktop shortcuts create a custom launcher(rightclick) and set the command to whatever you want a shortcut for

---

### Post by parkerskouson on 2011-07-08
Cool. thats exactly what i needeed. Thanks for the help.

---

### Post by IWantFroyo on 2011-07-08
> **srisharan said:**
> To remove the bottom gnome panel, just right click on it and click on the delete this panel option.Now to remove after the top one has also been deleted,yes there is a way but it will remove useful shortcuts like alt+F2.A better method is to open gconf-editor(alt+F2 or terminal)and got o apps>panel>levels>your_panel and autohide it and set the unhide delay to a big no(like 999999)

Nailed it. You could run
 ```
sudo apt-get remove gnome-panel
```but that will kill your Alt-F2, which is a very useful function.

To make desktop icons, you can just pull them down off the tree menus to the desktop.

---

### Post by srisharan on 2011-07-08
> **IWantFroyo said:**
> Nailed it. You could run
 ```
sudo apt-get remove gnome-panel
```
but that will kill your Alt-F2, which is a very useful function.

.
That is why hiding it almost indefinitely is better

---

### Post by parkerskouson on 2011-07-08
What i did for the desktop button was i got Docky and just installed a desktop button to it. Works really well. Would reccomend it for people who dont like unity.

---

