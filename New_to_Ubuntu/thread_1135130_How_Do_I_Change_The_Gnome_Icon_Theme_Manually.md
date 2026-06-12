---
title: "How Do I Change The Gnome Icon Theme Manually?"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by cafeinoz on 2009-04-24
How do i change the gnome icon theme by editing a text file or command?

---

### Post by cariboo on 2009-04-24
You can open ~/.gconf/desktop/gnome/interface, and edit *%gconf.xml, to change the name of the theme and icon set.

It would be much easier to right-click on the desktop, then select Change Desktop Background, next click the Themes tab then click the Customize button.

---

### Post by Tibuda on 2009-04-24
To find out the current theme in the terminal/script:
```
gconftool-2 -g /desktop/gnome/interface/icon_theme
```
To change it:
```
gconftool-2 -t string -s /desktop/gnome/interface/icon_theme Human
```
(replace Human with the icon theme name)

---

### Post by spillin_dylan on 2009-04-24
Is there a way to select some icons from some themes, and others from others, though?  Or does a person have to manually change the .svg and .png icon files manually?

---

