---
title: "Gnome-Panel-Transparent issue?"
date: 2009-09-09
forum: New to Ubuntu
---

### Post by Codix121 on 2009-09-09
Anyway to make the Gnome-panel (Top panel) actually transparent, when I go to properties, it only sets the middle of the panel transparent, it looks rather stupid... it doesn't full put the rest of it in transparent.

Anyone have any tutorials, links or knowledge on how I can make my top panel transparent (not fully, I know about the using a "transparent" image fix) but to make my black panel a bit transparent.

---

### Post by credobyte on 2009-09-09
Let us know what theme you are using ( panel transparency works with all the default Ubuntu themes ).

---

### Post by CatKiller on 2009-09-09
As credobyte implies, the appearance of the panel widgets is GTK-theme-dependent. You can either switch to a theme that does the panel properly or attempt to edit the theme that you otherwise want to use so that it too does the panel properly.

---

### Post by ankspo71 on 2009-09-09
Hi,

If you are able to use compiz 3D effects, there is a nice way to add transparency to panels, windows, start menus etc. I am trying this out now, and it is working out nicely.

First you will need to make sure 3d effects are enabled. Second, you will need to install CompizConfig Settings Manager. Your can install it through Synaptic Package Manager, or you can open up a terminal and type the following...

```
sudo apt-get install compizconfig-settings-manager
```

Next you run CompizConfig Settings Manager located in your System>Preferences menu.

Next navigate to, and enable, "Opacity, Brightness and Saturation".

Open those settings, and do the following:

In the opacity tab, click on new, and type in:
```
(name=gnome-panel)
``` 
and move the slider to 75%

Be VERY careful, because a value of 0% will make your panels 100% invisible, making them extremely difficult to use.

Unfortunately, this will effect both top and bottom panels.

You can also add entries for other parts of the desktop such as:

New:
(type=Menu | PopupMenu | DropdownMenu | Dialog | ModalDialog)
Value:85
-
New:
(type=normal)
Value:97
-
New:
(name=gnome-panel)
Value:75

This is how I prefer mine (so far).
I am attaching a screenshot to make it less confusing.

Hope this helps.
James

---

