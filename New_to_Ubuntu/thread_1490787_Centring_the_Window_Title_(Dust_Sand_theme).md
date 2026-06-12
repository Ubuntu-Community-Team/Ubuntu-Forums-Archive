---
title: "Centring the Window Title (Dust Sand theme)"
date: 2010-05-22
forum: New to Ubuntu
---

### Post by Jakey_TheSnake on 2010-05-22
Okay, so I've moved the window controls back over to the right via gconf-editor, all pretty usual stuff (though they should be on the right by default, of course), but now it's broken my window title centring. The text now displays on the very left of the title bar, which looks horrible. 

So how do I get it back to the centre? My spidey sense tells me I'll have to edit the usr/share/themes/Dust\ Sand/metacity\ 1/thingybob.xml, but I have no idea how.

---

### Post by cariboo on 2010-05-23
If you want your buttons on the right side, you don't have to edit a configuration file, Ambiance and Radiance are the only two themes with the buttons on the left, all th rest of the themes have the buttons on the right by default.

---

### Post by Jakey_TheSnake on 2010-05-23
I have my buttons on the right hand side, I need to centre the window title. At the moment it is on the very left of every window I open.

---

### Post by Jakey_TheSnake on 2010-05-23
Shameless self-bump.

---

### Post by Jakey_TheSnake on 2010-05-23
Shameless 2nd self-bump.

---

### Post by Jakey_TheSnake on 2010-05-23
Solved it myself. Go to the directory /usr/share/themes/*theme name here*/metacity-1/ then open metacity-theme-1.xml with gedit (may need root permissions, I was browsing with gksu nautilus at the time). Find the <-- Window Title --> or some such heading, look at the top two lines where it says ```
x="some number", y = "((width - title_width) / 2) `max` 0"
``` and replace the constant value of x with ```
((width - title_width) / 2) `max` 0
```. 

Thanks for all your help, folks *rolls eyes*

---

### Post by redoscar3 on 2010-05-24
Jakey......thanks for the info on how to center text in the titlebar.  Normally I would use emerald on my Ubuntu's but our laptop has a cheapy video card and will only support metacity.  I was working on dressing up my themes, liked Dust, but disliked the uncentered titlebar.  Your fix came just in time to make the change a painless process.  The laptop now looks pretty snappy in its new set of clothes.

Cheers!

Red

---

### Post by kohoutek1 on 2011-10-05
Yes, works fine in Natty, as well. Just remember that changes will appear after next log in.

---

