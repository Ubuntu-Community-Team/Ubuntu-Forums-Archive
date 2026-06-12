---
title: "Why cant I move items in folders?"
date: 2009-06-26
forum: New to Ubuntu
---

### Post by typos1 on 2009-06-26
It wont let me put items where I want them, only in alpha/numerical order, why??

I m viewing photos in a folder I copied from XP, theres no trouble viewing them but I want them in my order not what the OS wants, can I change this?-Thanks

---

### Post by Hamchan on 2009-06-26
Just right click any empty space in the folder and it'll give you a menu. Choose arrange items then click manually.

---

### Post by typos1 on 2009-06-26
Ah! I see! Thanks!

---

### Post by drs305 on 2009-06-26
Edit: See you are using "Icon view".  What Hamchan said!

In nautilus you can sort according to the following in "list view". I was hoping for a "none" option, but unfortunately not. This is from gconf-editor:
> 
name, size, type, modification_date

```
gconf-editor /apps/nautilus/icon_view/default_sort_order
```

There is a "manual layout" option in the icon view section (for layout, not sort). **[COLOR="DarkRed"]ADDED:[/COLOR]** Playing with the setting revealed it invokes the same properties in "icon view" as right clicking and selecting "manual".  Right click is easier on an individual folder, but if you wanted the default icon view to be manual for all folders the command, if anyone is curious , is:
```

gconftool-2 --type bool --set /apps/nautilus/icon_view/default_use_manual_layout "true"

```

---

### Post by typos1 on 2009-06-26
File browser has the same menu, I just didnt think of right clicking!

---

