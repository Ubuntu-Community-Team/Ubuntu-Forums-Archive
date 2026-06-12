---
title: "Transparent menus with Metacity compositing"
date: 2009-09-30
forum: New to Ubuntu
---

### Post by humphreybc on 2009-09-30
Hi guys,

I was wondering whether it is possible to have transparent menus with Metacity, when compositing is enabled?

In theory it should work, as compositing allows the terminal window to be see-through if you set it like this, so is there a way to set the menus at say, 90% transparency?

I don't want to use compiz.

---

### Post by keplerspeed on 2009-10-01
See here [http://ubuntuforums.org/showthread.php?t=1197529](http://ubuntuforums.org/showthread.php?t=1197529) for  transparent  menus and window borders.

However, not sure about transparent menus without compiz.. Might have to go hunting for a key in gconf-editor.

---

### Post by mcduck on 2009-10-01
> **humphreybc said:**
> Hi guys,

I was wondering whether it is possible to have transparent menus with Metacity, when compositing is enabled?

In theory it should work, as compositing allows the terminal window to be see-through if you set it like this, so is there a way to set the menus at say, 90% transparency?

I don't want to use compiz.

In theory that would be possible, but in reality it's not. The problem is that Metacity doesn't have any functionality to do that (like the "Opacity, Brightness and Saturation"-plugin for Compiz), so the applications themselves, or GTK, would have to tell the compositing manager to draw the menu windows transparent. And they don't have such option either..

(Gnome-terminal gets real transparency when compositing is available because the support is included in Gnome-terminal itself, it's able to recognize when there's a compositing manager available and then changes to drawing in RGBA colors.)

---

### Post by yoghie86 on 2011-10-13
use ubuntu software center and instal compiz

---

### Post by oldos2er on 2011-10-13
Closed, necromancy.

---

