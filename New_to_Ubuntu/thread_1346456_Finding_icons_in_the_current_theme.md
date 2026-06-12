---
title: "Finding icons in the current theme"
date: 2009-12-05
forum: New to Ubuntu
---

### Post by andypandy123 on 2009-12-05
I have installed the Mac4Lin theme and in my main menu, firefox appears with the normal icon. I want to change this, and can edit the menu settings, but don't know where the folder with the current icon theme is. can anyone help me?


thanks in advance.
andy

---

### Post by Ylon on 2009-12-05
Quickest way I can think about is:


terminal:
**sudo updatedb**
**locate -i Mac4Lin**



(**locate -i Mac4Lin | grep icon** if the list is too long **locate -i Mac4Lin | grep firefox** if you're looking just for this one)

---

### Post by endBc on 2009-12-05
Not sure about Mac4Lin but icon themes can be found in /usr/share/icons.

---

### Post by PocketDog on 2009-12-05
**/home/***yourusername***/.icons/Mac4Lin_Icons_v1.0/**

Or,

**Places > Home Folder > 'ctrl+h' > .icons/Mac4Lin_Icons_v1.0/**

---

