---
title: "Movie Player Opens Then Crashes"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by Rog3236 on 2009-04-26
This issue was reported after an upgrade to 9.04 from 8.10 Intrepid. One of the solutions offered was this:

Workaround to get it working: open gstreamer-properties. Then, Video tab, Default Output section. Change the Plugin from "Autodetect" to "X Window System (No Xv)" and close. This way, totem will play any video format.

I have no idea how you get to gstreamer to change it's properties. 

Thanks

---

### Post by Sealbhach on 2009-04-26
That's a terminal command.

Copy and paste  

gstreamer-properties

into the terminal and it opens up a window where you can do those things.

You can find the terminal in the Applications/Accessories menu.


.

---

### Post by steve101101 on 2009-04-26
+1

---

### Post by Rog3236 on 2009-04-26
Thanks it solved the problem.

---

### Post by steve101101 on 2009-04-26
glad everyone could help.

---

