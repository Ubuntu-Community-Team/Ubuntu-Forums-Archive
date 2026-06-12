---
title: "packing shortcut into hotkey?"
date: 2010-07-04
forum: New to Ubuntu
---

### Post by utnubuk on 2010-07-04
Hi, my question relates to Ubuntu/Gnome

If I want to enter the latin letter small o with dot below **[SIZE="4"]&#7885;[/SIZE]**, the requirement is the shortcut for unicode entry, CTRL+Shift+u, plus the actual unicode number 1ecd.

That shortcut hurts my wrist if using it more than 4, 5 times, so I want to pack the shortcut part into an assigned hotkey, preferably the right windows key. This means all I have to do then will be instead

CTRL+Shift+u + 1 + e + c + d
just
winkey + 1 + e + c + d

Gurchamap is not an option as it has only limited special letters/signs, or one has to go through the fonts which is all very time consuming. 



**************************************************************
What I've done so far:

I've installed XBindKeys and created .xbindkeysrc plus the GUI part.

Problem: XBindKeys-modified keys can launch programs/shellscripts, but it barks at me when trying to fix a shortcut to a key. I've tried different variants like control + shift + u or CTRL+Shift+u in the action field after having selected the windows button, but in the terminal it says sh: control: not found.

Another thing I tried was the gconf-editor, following an instruction which didn't exactly target my objective, but I really don't know *exactly* what has to be changed there to get to where I want to be. 

I've also looked at keyboard-layouts options tab, but none of available situations seemed to allow me to set the windows key to launch a shortcut.

---

