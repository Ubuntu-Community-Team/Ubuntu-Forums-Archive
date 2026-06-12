---
title: "Wine C:\ Virtual Drive Help"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by ranger5664 on 2008-12-03
I have installed wine and want to brows the virtual C:\ drive. However, when i click applications, go to wine, and click brows C:\, the menu disappears like it is supposed to be opening it, but never does. Can someone give me a path or a terminal command that i can use to get to the virtual C:\ drive?

---

### Post by Titan8990 on 2008-12-03
I don't have a system to check on but it should be located somewhere under the .wine directory in your home folder.

---

### Post by ranger5664 on 2008-12-03
Im looking and doing searches for the .wine directory but i cant seem to find it.

---

### Post by ranger5664 on 2008-12-03
Nevermind that last post... I got it i think.

---

### Post by Titan8990 on 2008-12-03
Try this:


cd ~/.wine/drive_c/

---

### Post by kestrel1 on 2008-12-03
Go to your home folder & select the View menu & then select Show Hidden Files.
Your .wine folder is near the bottom & there will be a folder called drive_c
Then you can browse the folders in there.

---

