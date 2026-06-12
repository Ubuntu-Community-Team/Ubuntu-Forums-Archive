---
title: "changing the ubuntu icon"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by cirabisi2009 on 2009-07-08
i've done this before, i want to change the ubuntu symbol into the apple symbol but i cant figure out where to find the icon. i went to home hit ctrl+h to reveal hidden and i thought it was in icons and isnt, and its not in theme!! where to i find this?

---

### Post by pirattrev on 2009-07-08
which icon are you talking about? the menu bar?

---

### Post by cirabisi2009 on 2009-07-08
> **pirattrev said:**
> which icon are you talking about? the menu bar?

yes.

---

### Post by clive littlewood on 2009-07-08
Hi

Switch your Mac on !!!!!!!!!!!!!     :lolflag:


Clive

---

### Post by cirabisi2009 on 2009-07-08
> **clive littlewood said:**
> Hi

Switch your Mac on !!!!!!!!!!!!!     :lolflag:


Clive

lol

---

### Post by NilsE on 2009-07-08
From memory I believe it is start-here.png (or SVG).

Since it is not in your home folder go to /usr/share/icons and it should be in either your current selected icons or human or gnome

---

### Post by Mornedhel on 2009-07-08
I just did this.

Type "locate start-here" in a terminal. Look for the file located in your theme's directory. Then copy-paste your own file in its place.

Apparently there's no other easy way to do this, since it's set by the theme.

You may need to log on/off again, or remove your menu and add it again in the panel.

---

### Post by VCoolio on 2009-07-08
It's the start-here icon in your icon theme in either ~/.icons or /usr/share/icons. Search for the folder scalable and then places.

Easier way is to start gconf-editor, browse to /apps/panel/objects, find the object that says "object_type      menu-object", check use_custom_icon and set the value for custom_icon for the path to the icon you want.

---

