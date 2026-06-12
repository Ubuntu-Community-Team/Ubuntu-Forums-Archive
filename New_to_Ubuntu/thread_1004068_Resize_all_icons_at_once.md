---
title: "Resize all icons at once"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by pHreaksYcle on 2008-12-06
How would I go about doing this? Command line, GUI, doesn't matter to me, I hate doing them all manually.

If no precise answer, any hints? I'm good at searching. . .

But perhaps not good enough. . .

Let me know, thanks!

---

### Post by drs305 on 2008-12-06
You can set the icon size for the desktop or in nautilus in at least three ways.

By far the easiest:

1. In nautilus, Settings, Preferences, View. Adjust the sizes to suit your desires.

Caution, geek alert:

2. Open gconf-editor and adjust the sizes.
Available sizes are: smallest, smaller, small, standard, large, larger, largest
```
gconf-editor /apps/nautilus/icon_view/default_zoom_level # nautilus icon view and desktop icons
gconf-editor /apps/nautilus/list_view/default_zoom_level # nautilus list view
gconf-editor /apps/nautilus/preferences/default_zoom_level # nautilus defaults
gconf-editor /apps/panel/toplevels/bottom_panel_screen0/size # bottom panel height
gconf-editor /apps/panel/toplevels/top_panel_screen0/size # top panel height

```

3. Command line: 
Available sizes are: smallest, smaller, small, standard, large, larger, largest
```

gconftool-2 --type string --set /apps/nautilus/icon_view/default_zoom_level 'standard' # nautilus and desktop icons
gconftool-2 --type string --set /apps/nautilus/list_view /default_zoom_level 'standard' # nautilus list view
gconftool-2 --type string --set /apps/nautilus/preferences /default_zoom_level  'standard' # defaults
gconftool-2 --type string --set /apps/panel/toplevels/bottom_panel_screen0/size '24' # bottom panel height pixels
gconftool-2 --type string --set /apps/panel/toplevels/top_panel_screen0/size '24' # top panel height pixels

```

---

### Post by pHreaksYcle on 2008-12-06
Sorry -

I was speaking of desktop icons.

---

### Post by drs305 on 2008-12-07
> **pHreaksYcle said:**
> Sorry -

I was speaking of desktop icons.

The answers are there, I just wasn't sure which one you wanted. The Desktop icons are set with the 'icon_view' commands above or Nautilus, Edit, Preferences, View, Icon View Defaults.

---

### Post by pHreaksYcle on 2008-12-07
Oh, I see, didn't notice that part, thought those were just for actual nautilus windows. Thanks!!

---

