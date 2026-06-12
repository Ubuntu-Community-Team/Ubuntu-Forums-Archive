---
title: "can't close open windows"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by xstryker on 2009-04-05
I just spent two days getting the cube effect to work, and finally did, but now when i open a window i can't close it by clicking the (X) in the corner of the page because its not there.  I'm to mentally drained to try and figure it out myself.

---

### Post by Fixman on 2009-04-05
> **xstryker said:**
> I just spent two days getting the cube effect to work, and finally did, but now when i open a window i can't close it by clicking the (X) in the corner of the page because its not there.  I'm to mentally drained to try and figure it out myself.

Open a terminal, and write:

```
 emerald --replace 
```

---

### Post by jimreynold2nd on 2009-04-05
Well, if you have the cube, then compiz is running as the window manager. You have to go to Advanced Desktop Effect Settings (ccsm or compizconfig-settings-manager) and enable "Window Decoration" and hopefully your window borders and controls will come back.
Cheers

---

### Post by Helios1276 on 2009-04-05
Just to add: Under Windows Decoration - Command, add the above line 'emerald --replace'. That is if you are indeed using Emerald.

---

