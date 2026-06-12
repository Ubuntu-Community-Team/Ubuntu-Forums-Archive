---
title: "Disable window list/panel tooltips/ pictures in 10.04"
date: 2010-08-26
forum: New to Ubuntu
---

### Post by spoovy on 2010-08-26
I currently have either tooltips or miniature pictures of the window appearing whenever i hover over a button in the window list, a la Windoze 7 or KDE4.  I don't want this annoying behaviour but can't seem to turn it off.

I have tried the obvious things, disabling tooltips and 'animations' in gconf-editor>apps>panel, but this makes no difference.  There doesn't appear to be any option within the panel or window list menus, or anywhere else I can find.  

Googling around came up with the same or similar problem(s) in much older Ubuntu releases but nothing relevant to 10.04.  Anyone care to help me out?

Thanks in advance

Spoov

---

### Post by arubislander on 2010-08-26
Looks like you have the *Window Previews * Compiz effect enabled. 
If you haven't already done so, install the CompizConfig Settings Manager (ccsm) you can find it in the Ubuntu Software Center.

Once installed you'll find it under: System>Preferences>CompizConfig Settings Manager in your main menu. Go to Extra's and uncheck the box next to Window Previews. Now you no longer have the miniature picture of the window appearing. You're still left with tool tips though, although the setting in gconf-editor might handle that once Metacity has regained command of the windowlist panel.

---

### Post by spoovy on 2010-08-27
Thanks arubislander, that got rid of the popup pictures.  The tooltips are still there, but they aren't as annoying as the pictures.

---

