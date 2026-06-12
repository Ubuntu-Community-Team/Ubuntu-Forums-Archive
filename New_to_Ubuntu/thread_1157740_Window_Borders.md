---
title: "Window Borders"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by TheCrazyAnon on 2009-05-13
Ok, I used emerald theme manager now for some reason all my window borders have dissappeared! I am searching for two days I cant seem to get them back, the borders and titlebar...Please.... someone...

---

### Post by ravi_buz on 2009-05-13
Try changing ur theme

---

### Post by TheCrazyAnon on 2009-05-13
Tried that, I even uninstalled and reinstalled the emerald manager...

---

### Post by lavinog on 2009-05-13
What happens when you disable desktop effects?
And after you re-enable them?

---

### Post by TheCrazyAnon on 2009-05-13
Nice.. when I disable the effects the title bars and borders are back on. But when i enable it again they go away...

---

### Post by Crafty Kisses on 2009-05-13
Do you have "Window Decorations" checked in Compiz? That's probably the problem. If you have Window Decorations checked and it's still not displaying the window borders then you might want to run the following in the Terminal and see if the borders reappear:
```
emerald --replace
```

---

### Post by Russell Burrows on 2009-05-13
Is there a conflict with gnome panel applet.

All my icons, panels went poof.....gone.
The fix for me was to check file system and navigate usr then to bin and then I opened gnome panel and hey! just like that my desktop icons and all of my gnome panels were back.

In other words check system monitor to see if gnome panel is on the list and if its not then get gnome panel wakey, wakey since its responsible for panels nice stuff on the desktop.

Hope this helps.

---

### Post by TheCrazyAnon on 2009-05-13
Yeah its on... the gnome-panel thing... thanks newez..

---

### Post by TheCrazyAnon on 2009-05-13
It doesn't do anything when I type emerald --replace, its just sits there...

---

### Post by Russell Burrows on 2009-05-13
At present Compiz relies on gnome window decorator to draw windows borders so you need to have window decorator running.

To check if all plugins are loaded correctly, open gconf-editor and navigate to apps>compiz>general>allscreens>options: 


And I think that your problem stems from a plugin not loading.

Hope this helps.

---

### Post by TheCrazyAnon on 2009-05-13
Thanks all for your help, but now it is screwed very much because I fiddled a bit... so am reinstalling ubuntu...

---

