---
title: "main menu bar"
date: 2010-03-08
forum: New to Ubuntu
---

### Post by GregD001 on 2010-03-08
Hello,
I lent my dell mini 9 to someone.
When I got it back the main menu is moved to the right side.
How do you move it back to the top?
I clicked on it and selected move.  then tried to move to the top.  but it did not work.
any help

---

### Post by audiomick on 2010-03-08
On mine ( Ubuntu 9.10 ) I have to right click on the panel, select properties, and select the position with the drop down that is called "orientation" or "position" or something like that. Mine is in German, and it is called "Ausrichtung"...

---

### Post by GregD001 on 2010-03-08
I have ubuntu 8.04.
when I right click on the main bar I get help, about, remove from panel, move and lock to panel.
I have tried the move, but it does not seem to work.

---

### Post by Jarmen_Deffs on 2010-03-08
I think from memory in 8.04 you had ro select move, then drag it to the top of the screen...?

---

### Post by drs305 on 2010-03-08
You are talking about having the entire panel on the right side (vertical) of your screen correct? 

It sounds like you may be right clicking on an app instead of a blank area of the panel. The easiest way to move it is to hold the cursor over a blank area of the screen for a moment, then left click the mouse and drag it to the top. Otherwise, in 8.04 you should be able to select Properties, Orientation to get the panel where you want it.

One of the problems when the panel gets put to the side is a lack of empty space if you have a lot of icons. There may not be enough room to actually click on an empty area. If this is the case, you will need to remove one or more of the icons. Select a large one such as the main menu or ones that are standard that you can easily add back after you move the panel back to the top.

---

### Post by GregD001 on 2010-03-08
thanks all.
I finally found this.  which works

type "gconf-editor" press enter
under app then panel, then toplevels, then click top_panel_screen0
find orientation and change it from right to top.

---

