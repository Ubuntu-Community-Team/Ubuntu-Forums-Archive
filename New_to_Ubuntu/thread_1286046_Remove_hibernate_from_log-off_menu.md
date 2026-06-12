---
title: "Remove hibernate from log-off menu?"
date: 2009-10-08
forum: New to Ubuntu
---

### Post by donsy on 2009-10-08
Is there a way to do it?

---

### Post by Daniel1994 on 2009-10-08
You can easily do this in ubuntu tweak.

Ubuntu Tweak>System>Power Management

---

### Post by donsy on 2009-10-08
> **Daniel1994 said:**
> You can easily do this in ubuntu tweak.

Ubuntu Tweak>System>Power Management

Ubuntu Tweak doesn't appear in my Synaptic Package Manager. How do I get it?

---

### Post by Daniel1994 on 2009-10-08
[www.ubuntu-tweak.com](www.ubuntu-tweak.com) 
then "downloads" and follow the instructions:)

---

### Post by philinux on 2009-10-08
Nice little app.

Another way is to use gconf-editor from Apps Sytem tools

or
1. press Alt + F2
2. type gconf-editor
3. browse to /apps/gnome-power-manager>general
4. uncheck can_hibernate
* right-click on the item and Set as Mandatory

---

### Post by carnagex420x on 2009-10-08
Thats how I do it... Ubuntu Tweak provides nice 1 click options to make life easy.

You want /apps/gnome-power-manager/general - BTW

---

