---
title: "gtkrc files are read only"
date: 2011-04-07
forum: New to Ubuntu
---

### Post by danm452 on 2011-04-07
Hi,

I'm running Ubuntu 10.04 (Lucid), and running emacs snapshot, I came across the  "CRITICAL **: murrine_style_draw_box: assertion `height >= -1' failed" error. I remember that this could be remedied by editing the gtkrc files in usr/share/themes. However, I ran into the problem that the files are read only. How can I edit the gtkrc files?

---

### Post by wep940 on 2011-04-07
Perhaps you have to be the super user to write the files?  Try sudo gedit <filename> and see if that works.

---

