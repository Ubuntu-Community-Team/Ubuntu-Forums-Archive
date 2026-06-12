---
title: "Disable Hardware Acceleration"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by madjackrogers on 2009-05-12
I'm running Ubuntu 8.04 and I enabled the option for Nvidia Hardware acceleration; now, when I boot up I see nothing at all except a thick, gradually darkening graying line.  Is there some way I can disable this from the terminal in safe mode?

---

### Post by Jazzy_Jeff on 2009-05-12
You should be able to go into safe mode and then go into System> Administration > Hardware Drivers. You should see yours in the list. Click on it and remove it.

---

### Post by madjackrogers on 2009-05-12
I may have mis-communicated the problem here; even in safe mode, I can't see anything.  I know it's there, it's just not being displayed.  I was hoping for something I could type into the root command prompt or whatever it's called.

---

### Post by madjackrogers on 2009-05-12
Actually, JazzyJeff's response was almost right on, in a way; I just need a way to do that from terminal, since I can't do it through the GUI.

---

### Post by madjackrogers on 2009-05-12
bump?  Is that acceptable here?  I'm sorry if it's not, I am just really anxious to get a fix for this so I can go back to using ubuntu.

---

### Post by madjackrogers on 2009-05-12
Figured it out!  To anyone else having this problem, just use recovery mode in GRUB, then pick the "repair X server" option. For some reason, that fixed it.

---

