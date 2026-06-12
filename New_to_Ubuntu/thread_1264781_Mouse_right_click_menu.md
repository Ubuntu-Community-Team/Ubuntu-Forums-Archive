---
title: "Mouse right click menu"
date: 2009-09-12
forum: New to Ubuntu
---

### Post by AndyP79 on 2009-09-12
Hi All,
Okay, so I am redoing everuthing again. I am not sure why, but I don't have any right click menu from the mouse?

---

### Post by swoody on 2009-09-12
Are you getting any reaction from right-clicks anywhere? Is this a universal thing, or is the right-click menu just not appearing in certain instances? Is this a problem only on your account, or on every user account on the computer? Also, are you using an external mouse, or a built-in-touchpad? If external, is it connected via bluetooth, IR, USB, or PS/2? Is the right-click work fine in any other OS besides Ubuntu?

Just right off the bat, have you tried restarting your computer? If that doesn't help, go to System>Preferences>Mouse, and try switching to a 'Left Handed' layout. Apply this, and attempt again to use both mouse buttons (now with the left handed layout, the buttons' functions will be swapped). Is the right-button on your mouse still failing to work, or is it the menu-function that is not working? (Basically trying to determine whether this is a hardware issue, or just an issue in Ubuntu)

Please try this out, and let us know how it goes :)

Woody

---

### Post by AndyP79 on 2009-09-12
Hi Woody,
 Thanks for the advice. I have tried restarting the computer. I tried the lefty right thing. And I have tried the both the touch pad and the USB mouse. It seems that when I right click in a window, I get that menu, but still not on my desktop. I am the only user on this computer, and I currently have no other OS on here.

---

### Post by swoody on 2009-09-12
Ah, so this is only an issue when you right-click on your Ubuntu desktop? But right-clicking in other windows/programs works fine?

---

### Post by swoody on 2009-09-12
Try this out...
Press atl+F2 so the 'Run' diagloge comes up. Type 'gconf-editor' and hit enter.

The new window that appears will have entries in a tree-type system on the left hand side. Just navigate to
Apps>Nautilus>Preferences. On the right hand side, make sure 'draw_desktop' is selected. If it's not, simply click the box to check it, and you can exit gconf-editor. Try restarting your computer, and see if the issue persists.

---

### Post by AndyP79 on 2009-09-12
I tried that, but that option is not there. Is there anywhere else to access that?

---

