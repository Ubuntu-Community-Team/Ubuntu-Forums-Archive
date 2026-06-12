---
title: "panel deleted"
date: 2010-07-26
forum: New to Ubuntu
---

### Post by thatguy93 on 2010-07-26
umm, i just deleted the panel on the top of the desktop. it has the menu's and all that jazz. How the heck do i get it back?

---

### Post by wojox on 2010-07-26
Reset the Panels. Run these two commands fron your terminal

```
gconftool --recursive-unset /apps/panel
```

```
pkill gnome-panel
```

---

### Post by theozzlives on 2010-07-26
Do you have a panel? Just right click on it and select new panel, then right click on the new panel and select add to panel to restore your menus, etc.

---

### Post by thatguy93 on 2010-07-26
sweet. thanks. how do i get the wifi signal indicator back too?

---

### Post by theozzlives on 2010-07-26
> **thatguy93 said:**
> sweet. thanks. how do i get the wifi signal indicator back too?

Add to panel > notification area.

---

### Post by thatguy93 on 2010-07-26
> **theozzlives said:**
> Add to panel > notification area.

nothing shows up

---

