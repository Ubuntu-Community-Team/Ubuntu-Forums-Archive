---
title: "No Min Max Buttons"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by 1devils1 on 2010-05-07
Hi,

Just upgraded to 10.4 - All seemed to go fine.

But I have no buttons on my applications (Min Max Close)

I have run gconf-editor and changed the button_layout to "menu:maximize,minimize,close" in hope that moving them would make them appear

This however did not work and my windows are still buttonless

Cheers

Paul

---

### Post by cosine352 on 2010-05-07
paste that in your terminal
> gnome-appearance-properties %F

now click on the theme and chose a theme (Ex: human) . see if this solves this problem.

---

### Post by Calash on 2010-05-07
Are you just missing the buttons or the entire window frame?

Issues with a replacement window decorator such as Emerald or Compiz will cause the frame not to show up.

---

### Post by 1devils1 on 2010-05-07
Hi Guys thanks for the quick respsonses.

Changed the theme. - No difference - Still no buttons

The window frame is there (The buttons are not)

---

### Post by 1devils1 on 2010-05-08
Okay Solved it. - Posted on this forum.

[I]sudo aptitude purge xubuntu-desktop && sudo aptitude clean && sudo aptitude update && sudo aptitude install xubuntu-desktop && sudo /etc/init.d/gdm restart


[/I]

---

### Post by rgsteele on 2010-05-08
> **1devils1 said:**
> Okay Solved it. - Posted on this forum.

[I]sudo aptitude purge xubuntu-desktop && sudo aptitude clean && sudo aptitude update && sudo aptitude install xubuntu-desktop && sudo /etc/init.d/gdm restart


[/I]

DO NOT follow these instructions unless a.) you are running Xubuntu as opposed to Ubuntu and b.) you have saved all your work, as it will kill all the applications you have open.

As Calash posted, the issue was likely with the window decorator. Merely setting Visual Effects to None from System>Preferences>Visual Appearance would likely have resolved it.

---

