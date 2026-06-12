---
title: "How to close a window and kill its process?"
date: 2009-11-27
forum: New to Ubuntu
---

### Post by vaibhav1 on 2009-11-27
Hi,

I have just installed opencv and compiled its laplace.c example file. The complied program displays the Laplace transform of a webcam's video stream... 

The program itself runs great, but when I close the program, the process still exists in the system monitor, but with a "sleeping" status. This means that if I want to run the program again (by clicking on it in the file browser), nothing happens, unless I specifically kill the process using the system monitor... is there any way I can avoid this problem, since it is a bit inconvenient.

Thanks

---

### Post by staf0048 on 2009-11-27
This is more of a bump than anything, but I run into this problem with a game I play in WINE every once in a while and it's very annoying.  Especially since the only way I know it didn't close properly the last time is after waiting 2 minutes for the thing to open the next time I want to play it.

I dont' know if our issues are related or not, but the only suggestions I can come up with are to exit the program using it's own exit routine (ie. file, close/quit) instead of just clicking the "X" on the upper right or utilizing "force quit" every time you close that app.  I leave the force quit icon on my panel for easy access.

---

### Post by Xarver on 2009-11-27
pkill appname should kill it.

---

### Post by vaibhav1 on 2009-11-27
thanks for the prompt reply - just wondering, how do you get the force quit icon to appear?

---

### Post by Muskegman on 2009-11-27
Right click on the panel and then select "add to panel" then select the "force quit" icon .Then select "add" and the force quit application should be on the panel all the time.

---

### Post by vaibhav1 on 2009-11-27
thanks

---

