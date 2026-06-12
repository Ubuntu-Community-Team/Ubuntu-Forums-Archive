---
title: "Free Snap equivalent?"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by FrostPhoenix on 2009-06-05
As a windows user, I really loved the functionality of Free Snap

[http://blueonionsoftware.com/FreeSnap.aspx](http://blueonionsoftware.com/FreeSnap.aspx)

This program creates hotkeys for quick window resizing, allowing users to snap a window edge to the edge of the screen by pushing Win + right or reposition a window in a different corner of the screen by using Win + one of the diagnol keys.

Free Snap's setup was extremely useful when I wanted to organize two windows to appear side-by-side on the screen with little hassle. I'm looking for more flexibility than simple Minimize/Maximize hotkeys provide.

I've searched on Google and on these forums to find out if Ubuntu/GNOME has any similar hotkey functionality built in or available as a package. The only results I've found involve holding the ALT key + right mouse button to resize a window with the mouse. That's not exactly what I'm looking for.

Is there any package that would add functionality similar to Free Snap, or is there a way to set something similar up inside GNOME's hotkey manager?

Thanks!

---

### Post by FrostPhoenix on 2009-06-08
I found a satisfactory solution to my need. For any other users that are interested:
Alt + F7 will allow you to move your current window with the keyboard
Alt + F8 will allow you to resize your current window with the keyboard

---

### Post by FrostPhoenix on 2009-06-11
And I found another solution, for anyone interested.

By installing the compizconfig settings manager for compiz (used in Ubuntu when you have any sort of visual effects activated in System > Preferences > Visual Effects > Visual Effects Tab), you can assign hotkeys that are similar to the functionality found in Free Snap.

Use this guide to get CompizConfig running on your computer:
(Source: [http://www.howtoforge.com/enabling-compiz-fusion-on-an-ubuntu-9.04-desktop-nvidia-geforce-fx-5200](http://www.howtoforge.com/enabling-compiz-fusion-on-an-ubuntu-9.04-desktop-nvidia-geforce-fx-5200) )

1) Check that 3D hardware drivers are installed on your system under System > Administration > Hardware Drivers. (I'm assuming that you need a discreet graphics card to run compiz.) If you make any changes to hardware drivers, reboot your computer before proceeding.
2) In the Synaptic Package Manager, find and install (along with dependencies):
simple-ccsm
3) Now, a new item will appear in the System > Preferences menu, called CompizConfig.
4) Find the Icon in the Window Management section called "Maximinumize" (except I'm sure I've spelled it wrong here.)
5) In that settings window, you can assign hotkeys to "Maximize to Left," "Maximize to Right," "Maximize to Top," and "Maximize to Bottom."

Also, if you like hotkeys for windows management, you may also be interested to learn that Compiz can be made to tile and cascade the windows open on your current virtual desktop. (This is useful when you want to have two file managers open right next to each other for easy file organization or when you want a terminal open on one side of the screen and a set of instructions open on the other side.)

To get tiled windows, go back into Synaptics Package Manager and install:
compiz-fusion-plugins-unsupported

After you install this, an icon for Tile Windows will appear in the Windows Management section of CompizConfig.

---

