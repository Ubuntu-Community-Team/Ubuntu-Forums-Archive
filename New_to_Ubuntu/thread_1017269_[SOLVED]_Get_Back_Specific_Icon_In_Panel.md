---
title: "[SOLVED] Get Back Specific Icon In Panel"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by RookieUbuntuUser58 on 2008-12-20
I accidentally removed my wireless connection and battery status icons from my upper panel. Is there any way to get those specific icons back? I checked add to panel but they have different icons from those. Its the stock Intrepid icons for wireless and battery status. Thanks in advance.

---

### Post by adult swim on 2008-12-20
in the add to panel menu its called notification area
you may need to restart your panel once you add it for it to show up
```
killall gnome-panel
```

---

### Post by RookieUbuntuUser58 on 2008-12-20
> **adult swim said:**
> in the add to panel menu its called notification area
you may need to restart your panel once you add it for it to show up
```
killall gnome-panel
```

Thanks that worked.

---

### Post by abn91c on 2008-12-20
> **boost3d23 said:**
> I accidentally removed my wireless connection and battery status icons from my upper panel. Is there any way to get those specific icons back? I checked add to panel but they have different icons from those. Its the stock Intrepid icons for wireless and battery status. Thanks in advance.
That depends on whether you have a custom theme installed, then the icons will be different. go to system>preferences>appearance then click on the customize button then on the icons tab and enable a new icon theme

---

