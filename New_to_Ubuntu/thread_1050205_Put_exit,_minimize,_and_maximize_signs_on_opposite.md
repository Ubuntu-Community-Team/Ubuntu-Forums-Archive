---
title: "Put exit, minimize, and maximize signs on opposite sides.."
date: 2009-01-25
forum: New to Ubuntu
---

### Post by gymophett on 2009-01-25
I installed a mac theme package a few days ago and it wouldn't let me uninstall it so I just deleted all the files. Everything is mostly normal now. But the exit signs and stuff are on the opposite side (left side) and I hate it! Can someone please tell me how to change it.. It's getting on my last nerve. 
Thanks :)

---

### Post by diablo75 on 2009-01-25
Have you tried going to System>Preferences> Appearance and selecting a different theme?

---

### Post by mc4100 on 2009-01-25
Applications -> Accessories -> Terminal:
```
gconftool-2 -s  --type string  /apps/metacity/general/button_layout  menu:minimize,maximize,close
```

---

### Post by gymophett on 2009-01-25
> **mc4100 said:**
> Applications -> Accessories -> Terminal:
```
gconftool-2 -s  --type string  /apps/metacity/general/button_layout  menu:minimize,maximize,close
```

Thank you soo much :)

---

