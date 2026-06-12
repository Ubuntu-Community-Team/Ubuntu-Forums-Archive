---
title: "Which effect makes title bar transparent?"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by mvalviar on 2009-04-24
By default whenever I have desktop effects on inactive windows title bars are transparent? Which effect can I toggle to turn this effect on and off? Is there a way to modify the transparency of the title bar?

Thanks, 

Marco Enrico Alviar

---

### Post by Dileeshvar on 2009-04-24
Hi,

If you are using emerald theme manager then you are
using the glass effect I believe you can change it by
selecting another theme.
This helps if you are using emerald.

---

### Post by mvalviar on 2009-04-24
I don't have emerald. I believe its with either metacity or compiz. Any other ideas guys?

---

### Post by Dileeshvar on 2009-04-24
oh okay then it is the problem with metacity just check it out

---

### Post by MyR on 2009-04-24
No the transparency is due to compiz.  I don't think the transparency ("compositing") can be disabled but you can turn off compiz by switching to metacity.

peace

EDIT:  this might help: [http://ubuntuforums.org/showthread.php?t=864564](http://ubuntuforums.org/showthread.php?t=864564)

---

### Post by Godly on 2009-04-24
> **Dileeshvar said:**
> oh okay then it is the problem with metacity just check it out

Lol.... check what out?

---

### Post by durand on 2009-04-24
First a definition of the terms...

Compiz = The engine that does the effects and calls emerald or another suitable program to do the window management.
Metacity = Window Manager
Emerald = Window Manager

If you have desktop effects enabled and it's working, then you are using compiz and emerald. Otherwise you are using metacity.
Emerald is what you need to look at to change your titlebar transparency. Press Alt+F2, run emerald-theme-manager. This will load the program used to manage your themes and stuff. If you look at one of the tabs, you may be able to change your transparency settings however it depends on what theme you use.
You can look [here]("http://gnome-look.org/index.php?xcontentmode=102&PHPSESSID=9fe81f9aaabf50f21397ea87e2028a53") for more emerald themes.

---

### Post by mvalviar on 2009-04-24
> **MyR said:**
> No the transparency is due to compiz.  I don't think the transparency ("compositing") can be disabled but you can turn off compiz by switching to metacity.

peace

EDIT:  this might help: [http://ubuntuforums.org/showthread.php?t=864564](http://ubuntuforums.org/showthread.php?t=864564)

Eureka! Thanks alot! 

Why is it that whenever I can't find something I can always expect to find it in gconf-editor.

---

