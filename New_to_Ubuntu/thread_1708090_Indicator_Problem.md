---
title: "Indicator Problem"
date: 2011-03-16
forum: New to Ubuntu
---

### Post by Avidanborisov on 2011-03-16
Hi Everyone!
Recently I installed the recent-notifications indicator but for some unknown reason every time I power on ubuntu I see this indicator twice. This can be solved by removing one indicator (that actually removes both) and then in "Add to Panel" put it again.
But, I hate to do it every time, so, any ideas?

---

### Post by cap10Ibraim on 2011-03-16
gnome panels never "just worked" !

---

### Post by Avidanborisov on 2011-03-16
What do you mean?

---

### Post by Frogs Hair on 2011-03-16
Try to restore to defaults and then try to add your indicator.```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

---

