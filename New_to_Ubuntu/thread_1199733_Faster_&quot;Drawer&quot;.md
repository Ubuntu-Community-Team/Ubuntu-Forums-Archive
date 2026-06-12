---
title: "Faster &quot;Drawer&quot;"
date: 2009-06-29
forum: New to Ubuntu
---

### Post by powel212 on 2009-06-29
I have a Drawer on my taskbar with all most commonly used apps in it.

when I click on it it opens half way for 1 second then opens all the way.

Is there a way to get it to open all the way when I first click it?

Thanks

Powel

---

### Post by oldos2er on 2009-06-29
You can try this:
```
gedit ~/.gtkrc-2.0
```and add ```
gtk-menu-popup-delay = 0
``` You may need to logout and log back in for it to take effect.

---

### Post by powel212 on 2009-06-29
Thank you.

Worked perfectly

Powel

---

