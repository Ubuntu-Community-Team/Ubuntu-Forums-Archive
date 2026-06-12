---
title: "Applications (Custom menu) dropdown won't open"
date: 2009-05-22
forum: New to Ubuntu
---

### Post by supermooshman on 2009-05-22
My "Applications" drop down menu won't open when I click it.
only a small square comes up.

also my desktop does not have any icons anymore (although there are things when I look at it with Nautilus) + right clicking on my desktop to get the right click menu (ie to make a launcher) doesn't work either.

anyone who can solve this mystery?
Many thanks

---

### Post by keplerspeed on 2009-05-22
Sounds like your nautilus desktop is disabled. Open a terminal, type this command:

> gconf-editor

In the new config window go to apps>nautilus>preferences and ensure show_desktop is ticked.

Does the generic drop down menu work fine? Ie right click on task bar, add to panel and add the ubuntu menu.

---

### Post by supermooshman on 2009-05-22
Halleluia it worked,

the generic menu does work, but it does not show the applications (don know if this is normal as I never tried this before)

---

