---
title: "Installing Vista Transformation Pack"
date: 2011-08-14
forum: New to Ubuntu
---

### Post by Orcris on 2011-08-14
I downloaded the Vista Transformation Pack ([http://gnome-look.org/content/show.php/Vista+Transformation+Pack+for+GNOME?content=63106](http://gnome-look.org/content/show.php/Vista+Transformation+Pack+for+GNOME?content=63106)), but I have no idea how to install it. Can someone give me simple instructions to install it on Ubuntu 11.04?

---

### Post by greenelf on 2011-08-14
> description:
This pack contents:

-vista emerald theme
-aero icons 0.5
-vista login 1.0
-linsta gtk theme (modified)
-linsta black plastic
-ubuntu-grass wallpaper
-start buttons
-vista startup sound
-vista-panel

for install all themes you need beryl with emerald, and gnome.

Vista emerald theme installation:
You need open emerald and import the theme.

Vista login 0.5 installation:
Open "/usr/bin/gdmsetup" as root and push the "local" tab, then push add and select the theme.

Start logos installation:
1) start "gconf-editor" in the terminal.
2) under apps > panels > objects > object_x, where x is the number of the "object" that is type "menu-object", check 'use_custom_icon' on the right and give a path to the icon under 'custom_icon'and refer to the logo.

Panel.png installation:
Secoundary button, propierties in the panel and select this file.

read!

---

