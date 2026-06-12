---
title: "Prevent Grouping of Volumes under &quot;Removable Media&quot; in Places"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by LordKelvan on 2008-12-03
Hi:

I've noticed that if I have too many removable volumes (these are all SATA drives installed in my case, and not USB drives), Ubuntu will group them under an entry called Removable Media in the Places menu.  This is sort of annoying, since now I have to go to a sub-menu to access the drives.

Can someone tell me how to change this behaviour so that all of my other drives are present as (top-level) entries in the Places menu, and not stuck in a sub-menu?

Cheers,
LK

---

### Post by LordKelvan on 2009-11-09
Bump

---

### Post by mc4man on 2009-11-09
You need to build the gnome-panel source and before building edit the number of 'bookmarks' (default is 5, karmic has upped the default to 8

Basic idea here (editing the defines is easiest way, the file to edit is 
/gnome-panel/panel-menu-items.c

[http://ubuntuforums.org/showthread.php?t=1066964](http://ubuntuforums.org/showthread.php?t=1066964)

I prefer to not build as described there (./configure, make, make install), but instead use the debian/rules and build as packages 
This way you keep the install as a re-install of the package(s)

Screen shows what's built on karmic,(pretty much the same for other versions), only the gnome-panel package really needs to be installed (I also upped the version by one (from 6 to 7) in the /debian/changelog, this way it won't be updated by the repo package, if gnome-panel is updated then I'd see an update and could either lock the current one or redo.

(even though when building the source as the same package as the repo, the repo one is seen as an upgrade



(( if using karmic, then rather than edit the .c file, just go into /debian/patches and change the number from 8 to what you need in patch 71_change_bookmark_...., then build using debian/rules
```

Index: gnome-panel-2.28.0/gnome-panel/panel-menu-items.c
===================================================================
--- gnome-panel-2.28.0.orig/gnome-panel/panel-menu-items.c	2009-09-24 10:52:12.000000000 +0200
+++ gnome-panel-2.28.0/gnome-panel/panel-menu-items.c	2009-09-24 10:52:32.000000000 +0200
@@ -62,7 +62,7 @@
 #define NAMES_DIR               "/apps/nautilus/desktop"
 #define HOME_NAME_KEY           "/apps/nautilus/desktop/home_icon_name"
 #define COMPUTER_NAME_KEY       "/apps/nautilus/desktop/computer_icon_name"
-#define MAX_ITEMS_OR_SUBMENU    5
+#define MAX_ITEMS_OR_SUBMENU    [COLOR="Blue"]8[/COLOR]
 
 G_DEFINE_TYPE (PanelPlaceMenuItem, panel_place_menu_item, GTK_TYPE_IMAGE_MENU_ITEM)
 G_DEFINE_TYPE (PanelDesktopMenuItem, panel_desktop_menu_item, GTK_TYPE_IMAGE_MENU_ITEM)
```

---

### Post by LordKelvan on 2009-11-09
Wow, thank-you very much for your effort.  Unfortunately, I'm not too comfortable with compiling and installing my own gnome-panel, so I think I'll just stick with the current behaviour.

---

