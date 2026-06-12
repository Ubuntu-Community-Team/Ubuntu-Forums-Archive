---
title: "Icon size adjustment"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by Yed Ied on 2009-08-18
I have looked through the forum and can't find how to do this.  Ubuntu 9.04, a little help please. Thanks

---

### Post by RedSingularity on 2009-08-18
Right clicking the icon and doing a "stretch icon" option?  You mean like that.?

---

### Post by drs305 on 2009-08-18
In nautilus, Edit, Preferences, Views tab: Icon View.

You can also set them via gconf-editor: 
```
gconf-editor /apps/nautilus/icon_view/default_zoom_level
```

---

