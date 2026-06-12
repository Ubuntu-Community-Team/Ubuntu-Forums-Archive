---
title: "OpenOffice software fonts too large"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by J.K on 2009-05-19
Hey,

I just recently started using xubuntu (9.04). One thing I've noticed in Calc is that the fonts used in the menu and in the row/column numbers and letters are way too big. Is there any way to shrink them down to the a more natural size (like the size of the program's title and filename)? Right now they're pretty near to twice as tall as the font in the title. It's just a bit awkward looking at it, since I use OOo a lot. I've seen ways of changing fonts used within the program, but nothing for this in particular.

J.K

---

### Post by john.nicholls on 2009-05-20
Tools | Options | View | Scaling should give you what you want.

---

### Post by oOarthurOo on 2009-05-20
Try installing the openoffice gtk component. Do, ```
sudo aptitude search openoffice | grep gtk
```
Install the gtk thingy that pops up. Ignore the gnome one, it's just a virtual package.

---

