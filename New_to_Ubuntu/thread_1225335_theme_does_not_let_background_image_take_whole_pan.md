---
title: "theme does not let background image take whole panel"
date: 2009-07-28
forum: New to Ubuntu
---

### Post by libihero on 2009-07-28
is there any way to make it so that some themes allow the background of the panel take the whole panel, instead of some like shown:

---

### Post by 67GTA on 2009-07-28
The theme your trying to use has a panel image it uses by default. You can find the theme folder in /usr/share/themes/name_of_theme/gtk-2.0/gtkrc. You need to edit the gtkrc file and comment out the panel section or change the path to the panel image you want. Not all themes have a default panel image.

---

### Post by libihero on 2009-07-29
Thanks!!

---

