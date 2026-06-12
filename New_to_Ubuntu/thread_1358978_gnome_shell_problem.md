---
title: "gnome shell problem"
date: 2009-12-19
forum: New to Ubuntu
---

### Post by sudhir k yadav on 2009-12-19
hi there,

i have installed gnome shell.Every time i have to give command gnome-shell -replace to start gnome shell after boot. I have read somewhere in ubuntu forum that if i can change to mutter in window manager then gnome-shell will be set as default desktop. But when i did so my mouse pointer has been disappeared!!! it appears that pointer is below the gnome-shell. When i tried to deselect the mutter option in window manager,my panel has disappeared.Can some body help??? How can i bring my mouse pointer back if i want gnome-shell to my default desktop??? and how can i set gnome-shell as default desktop without any complication??

thnaks

sudhir:lolflag:

---

### Post by wojox on 2009-12-19
If you want to make it your default, put "gnome-shell --replace" in your Startup Items

Be aware that there is currently a bug with the cursor being hidden in panel or overlay---the workaround is ALT & F2 to bring up a run dialog & type in "restart"--the shell will restart & grab your cursor.

---

### Post by sudhir k yadav on 2009-12-20
hi wojox,

i have tried what u have suggested but it didn't work!! I went to the system>preferences>startup application and added gnome-shell -replace in startup items but when i rebooted nothing happened.Am i doing something wrong?? can u suggest me in detail how to do it?? is there is any alternative??

thanks
sudhir:confused:

---

