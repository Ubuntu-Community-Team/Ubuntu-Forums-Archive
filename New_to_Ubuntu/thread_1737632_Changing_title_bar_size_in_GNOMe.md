---
title: "Changing title bar size in GNOMe"
date: 2011-04-23
forum: New to Ubuntu
---

### Post by gaurish108 on 2011-04-23
I have ubuntu 10.10. How does one decrease the size of a window title bar in GNOME? 

There does not seem to be a simple way to me

---

### Post by Jest3r on 2011-04-26
You can change the size of the font for the title bars, this will change the size... The smaller the font the smaller the title bar.


 $ gconf-edit
 /apps/metacity/general
 titlebar_font
 click on "Ubuntu Bold 11" and change the number.


There might be a simple way, but i have been playing with the gconf editor, so its fresh in my mind.

edit. I guess this is easier...
[LIST]
[*]System > preferences > appearance
[*]3rd Tab "Fonts"
[*]Change "window title font"
[/LIST]

---

