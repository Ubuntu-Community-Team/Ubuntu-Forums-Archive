---
title: "Shadows in Compiz Fusion"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by GepettoBR on 2009-04-15
Hello, all

Attached is a screenshot of my desktop. I like it simple and devoid of icons, save for when I mount something to /media, in which case I stretch the icons real big. </rant>

Anyways... I've looked around the settings in CCSM and I didn't find where I disable the shadows bordering Conky and the gnome-panel. I'd prefer disabling only these two shadows, but if there's only a global option that works too. They really get in the way of the look I'm after.


P.S.: I like to give credit where credit is due, so here's the source for the wallpaper: [http://zenibyfajnie.deviantart.com/art/New-Wave-99681996](http://zenibyfajnie.deviantart.com/art/New-Wave-99681996)

---

### Post by damis648 on 2009-04-15
For the gnome panel, go into CCSM and go to the 'window decoration' plugin. Change the shadow windows field to
```
any & !Dock
```
and for conky, go into your conkyrc and change the window type to
```
override
```

:popcorn:

---

### Post by GepettoBR on 2009-04-15
> **damis648 said:**
> For the gnome panel, go into CCSM and go to the 'window decoration' plugin. Change the shadow windows field to
```
any & !Dock
```
and for conky, go into your conkyrc and change the window type to
```
override
```

:popcorn:

Thank you so much! Flawless victory.

The "override" setting made conky ignore the panel and it shifted up, eating half my title. adding ${voffset 10} before the text solved that little hindrance, though.

New screenie. Much cleaner.

---

