---
title: "Moving the minimize, restore, X from left to right.."
date: 2010-05-04
forum: New to Ubuntu
---

### Post by Epedemic on 2010-05-04
After upgrading to Ubuntu LTS, or LT, or w/e it was called, it moved the top menu bar items to the left. Like the X, minimize, and restore are now on the left side instead of the right side. Anyone know how I can move that to the right side? I did a search on the forum but couldn't find anything on it.

edit: not sure how to change the [ubuntu] tag so I just edited the title.

---

### Post by Didius Falco on 2010-05-04
To move the window buttons back to the left, enter the
following in a Terminal window WITHOUT sudo:

```
gconftool-2 --type string --set /apps/metacity/general/button_layout "menu:minimize,maximize,close"
```

Alternatively, if you use Ubuntu tweak, it will do it for you in a gui.

Regards,

Didius

---

### Post by spaik on 2010-05-04
+1 ubuntu tweak

---

### Post by Epedemic on 2010-05-04
Thanks a lot my good sir. :D

---

### Post by madjr on 2010-05-04
ubuntu tweak :)

[http://www.getdeb.net/updates/Ubuntu/10.04/?q=ubuntu-tweak](http://www.getdeb.net/updates/Ubuntu/10.04/?q=ubuntu-tweak)

---

