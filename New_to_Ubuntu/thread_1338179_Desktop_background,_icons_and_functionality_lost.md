---
title: "Desktop background, icons and functionality lost"
date: 2009-11-26
forum: New to Ubuntu
---

### Post by profeta81 on 2009-11-26
Hello all!

Since a couple of days I seem to have lost all the desktop usual functionalities such as changing the wallpaper, the icons have disappeared and the menu that appeared with the right click doesn't appear anymore. I don't know what cosed the problem, I remember I fiddled a bit with the preferences such as window decorations, themes, resolution and visual effects...

anyone any idea how to solve this issue? can anyone point me to a page with the solution?

many thanks :)
Lorenzo

---

### Post by 0cton on 2009-11-26
try disabling compiz and see what happens.
are you sure you haven't disabled GNOME decorator so you can get 4 wallpapers on different screens?

---

### Post by Grenage on 2009-11-26
Run gconf-editor (can type that into a terminal), then go to:

Apps/Nautilus/Preferences

Ensure that show_desktop is ticked.

---

### Post by profeta81 on 2009-11-26
> **0cton said:**
> try disabling compiz and see what happens.
are you sure you haven't disabled GNOME decorator so you can get 4 wallpapers on different screens?

hi

mh... disabling compiz? is it enough to select "no visual effects" from the apparence preferences? I tried that but didn't change much

As to your second question... I don't know, well, I can still change the theme, fonts and interface (I'm referring to the apparence preferences again..), It's just the desktop...

cheers

---

### Post by profeta81 on 2009-11-26
> **Grenage said:**
> Run gconf-editor (can type that into a terminal), then go to:

Apps/Nautilus/Preferences

Ensure that show_desktop is ticked.

Ok thanks!!

well, It actually was ticked, so I unticked it and ticked it again and all worked fine!

Don't know what exactly was the problem, but it's ok now ;)

thanks again!
Lorenzo

---

### Post by Grenage on 2009-11-26
No problem; I once ran into the same issue myself after dabbling with GUI settings.

---

