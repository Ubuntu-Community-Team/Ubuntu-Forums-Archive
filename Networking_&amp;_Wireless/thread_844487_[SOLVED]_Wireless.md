---
title: "[SOLVED] Wireless"
date: 2008-06-29
forum: Networking &amp; Wireless
---

### Post by RMD94 on 2008-06-29
Hey Guys,

How can i scan for wireless network on Ubuntu Hardy (Eee PC).

plz help me!!!!!!!!!!!



-Rajas

---

### Post by untermensch on 2008-06-29
Just click on the nm-applet in the top right hand corner of the screen. (the two computer screens) if there isn't one open a terminal and type sudo nm-applet, and it'll show up.

---

### Post by Kevbert on 2008-06-29
As an alternative, go to terminal and type
```
iwlist scanning
```

---

### Post by RMD94 on 2008-06-29
> **Kevbert said:**
> As an alternative, go to terminal and type
```
iwlist scanning
```

after typing that i get 

lo    Interface doesn't support scanning


eth0  Interface doesn't support scanning

---

### Post by untermensch on 2008-06-29
Did you try just clicking on your nm-applet?

---

### Post by Kevbert on 2008-06-30
Please post what you get with the terminal command
```
iwconfig
```

---

