---
title: "Moving Window Border Icons to Left"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by Brendantb on 2009-11-21
I have moved from using Xubuntu with Xfce, to Ubuntu 9.10. 

For the life of me I can't see how to reposition the window border icons, the open, close and minimise icons at the top of a window, to the left hand side of the window border, as I am used to in Xubuntu. Is there a way of doing this?

---

### Post by mlentink on 2009-11-21
Go to 
Applications>System Tools>Configuration Editor

Select
Apps>Metacity>General

Search for the entry "button_layout"

Change the text to:

```
minimize,maximize,close:menu
```

Obviously, you could change the order if you want to

---

### Post by Brendantb on 2009-11-21
Thank you for the prompt reply. 

Your solution solved my problem, though it is puzzling that this isn't an option in the appearances menu. 

For the benefit of others, like myself, not familiar with linux, the configuration editor may not show under the applications>system tools menu, as it may be hidden by default in some downloads. You can then access the editor from a terminal window, (under applications>accessories,) by typing in:

gconf-editor

---

### Post by Rodu on 2010-05-02
> **mlentink said:**
> Go to 
Applications>System Tools>Configuration Editor

Select
Apps>Metacity>General

Search for the entry "button_layout"

Change the text to:

```
minimize,maximize,close:menu
```Obviously, you could change the order if you want to

I love this power you can have in configuring Gnome and Ubuntu!:guitar:

---

### Post by rakslice on 2010-10-19
First you can visit "Appearance Preferences" for a bit of comic relief.

---

### Post by quantum8 on 2010-12-16
thanks mlentink, the solution worked perfectly.

Hopefully the appearance control panel gets a facelift one day, the configuration editor reminds me too much of regedit!

---

### Post by Dafne Saqueti on 2012-02-20
Or, even easier, using terminal:

```

$ gconftool --type string --set /apps/metacity/general/button_layout "menu:minimize,maximize,close"

```

---

### Post by philinux on 2012-02-20
Old thread Closed thanks.

---

