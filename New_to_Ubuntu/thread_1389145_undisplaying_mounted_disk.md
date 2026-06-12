---
title: "undisplaying mounted disk"
date: 2010-01-24
forum: New to Ubuntu
---

### Post by 1991sudarshan on 2010-01-24
how to undisplay the mounted disks on the desktop in kubuntu?

---

### Post by rbscairns on 2010-01-24
In beginners terms, here is what I did when I had the same problem in Ubuntu 9.10-

    * Alt+F2 (opens the Run Application)
    * Type gconf-editor (for the Configuration Editor)
    * Click Run (opens the Configuration Editor window)
    * Expand the apps entry
    * Expand the nautilus entry
    * Select desktop
    * Deselect the volumes_visible option
    * Close the Configuration Editor window

These steps stop ALL volume icons from appearing on the desktop.

I hope this works for you.

---

