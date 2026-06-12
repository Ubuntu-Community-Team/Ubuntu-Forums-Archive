---
title: "How to  edit/modify themes?"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by treesurf on 2009-03-18
I recently installed an awesome new theme (Shiki Colors), but would like to modify it slightly.  The window title bars are a bit tall for me and I would like to make them shorter to maximize screen space.  

Are there any tutorials or resources on how to learn to edit this sort of thing?  Is there a conf file that has these parameters in it where I could just easily adjust the pixel count of the title bar, the same way I can with the gnome panel?

thanks

---

### Post by kaixi on 2009-03-18
I believe you can do it by selecting the theme and clicking Customize and I've never customized any themes as I find the default one to be quite beautiful.

---

### Post by tyroeternal on 2009-03-18
Here is a good general tutorial for you :)

[http://live.gnome.org/GnomeArt/Tutorials/GtkThemes]("http://live.gnome.org/GnomeArt/Tutorials/GtkThemes")

---

### Post by mcduck on 2009-03-18
Actually youd need a tutorial for Metacity themes instead of GTK, since it's the window border you want to change.

Sadly, that's even more complex than GTK themes are..
[http://developer.gnome.org/doc/tutorials/metacity/metacity-themes.html]("http://developer.gnome.org/doc/tutorials/metacity/metacity-themes.html")

You should find the theme files in ~/.themes/YOURTHEME/metacity/.

---

### Post by treesurf on 2009-03-18
Thank you!

---

### Post by treesurf on 2009-03-18
Oh boy, this is a bit more complicated than I thought it would be. Can I edit the theme while it is in use or should I be running a different theme and switch back and forth to check the effects of my changes?

---

### Post by mcduck on 2009-03-19
You won't see any changes in the theme until you reload it (by changing to some other theme and back again).

I recommend making a copy of the original theme, renaming it and editing that instead of the original.

---

### Post by treesurf on 2009-03-19
Thanks McDuck.  Tweaking away here!

---

