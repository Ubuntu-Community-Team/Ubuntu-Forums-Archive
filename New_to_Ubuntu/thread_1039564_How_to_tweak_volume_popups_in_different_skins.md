---
title: "How to tweak volume popups in different skins?"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by 11010110 on 2009-01-14
Hey all,

I picked up this new skin and everything is perfect save one thing. You know the little popup with the white speaker that you get when you change the volume level? I liked that one and it was replaced with a new looking one when I changed the skin. Does anyone know how I could go about changing JUST this part of the skin? It isn't in any of the options that I have come across. Its a GTK2 skin. Would I have to edit the skin itself? And if so how? 

Thanks everyone in advance! Any help is appreciated!

Its the little things that drive me nuts lol

EDIT: I narrowed it down to find that it was actually being controlled by the ICON SET that was being used. I am looking through all of the different pictures in the folders in the icon set but i cannot find the one im looking for...

---

### Post by laurielegit on 2009-01-14
Well for KDE the directory where the graphics are kept is /usr/share/kde4/apps/kmix/pics, and you can probably edit the .xml files in /usr/share/kde4/apps/kmix/profiles to change colour and stuff. Sorry I don't know about gnome, but it's probably somewhere in /usr/share/themes/your theme name.

Good luck,

Laurie

---

### Post by 11010110 on 2009-01-14
I have Gnome sorry i should have been more specific.

---

### Post by 11010110 on 2009-01-14
well i managed to figure it out! i couldnt find the one from the human theme so i took a screenshot and fashioned my own! lol works like a charm! only one thing though.... now i have a sort of hybrid volume thing in on the pannel up top. depending on the volume level its either the one that came with the icon set or the one i made. I cant seem to get that one working. I am using black-white 2 gloss icon set. if anyone could help me out id appriciate it! thanks everyone

---

### Post by 11010110 on 2009-01-14
got it! al it needed was a removal and replacing of the panel indicator.

---

