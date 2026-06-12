---
title: "inode/directory instead of application/x-desktop"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by Macinbomzh on 2009-11-03
I would like to know if there is a way to put shortcuts of directories on the desktop.
As I have noticed, windows allows to drag items into shortcuts and the items appear inside the directory, in ubuntu aswell but i cannot create my own shortcuts.

---

### Post by Peter09 on 2009-11-03
Well there is this way:

Using Nautilus navigate to the place where your existing folder is. Right click and select the 'make link' option. This will create a link to your folder. Drag the link to where you want it to be.

Might be worth experimenting with.

---

### Post by jchiar on 2009-11-03
Have you tried the Settings>Preferences>Main Menu or Keyboard Shortcuts. I know that is not an actual answer, but it is a start to a solution.

---

### Post by Macinbomzh on 2009-11-03
What you suggest works for folders. is there a way to make it also work for places such as trash:/// ?
also is there a way to remove the annoying arrow top right of the icon ?

---

### Post by Peter09 on 2009-11-03
It will work for files as well. If you are trying to get the trash bin to show on your desktop use

```
gconf-editor
```

then navigate to apps->nautilus->desktop and tick the trash visible box.

---

### Post by Macinbomzh on 2009-11-03
Exactly what i looked for! Thanks :D

---

