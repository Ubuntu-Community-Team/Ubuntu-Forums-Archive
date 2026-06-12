---
title: "cannot change visual effects"
date: 2010-04-09
forum: New to Ubuntu
---

### Post by infestor on 2010-04-09
in appearance preferences>visual effects i am stuck with **none** setting. whenever i click on **normal** or **extra** ubuntu searches for drivers and asks me whether to keep the new or previous setting but when i say ok it gets frozen!
any ideas to solve this issue?

---

### Post by Locke_99GS on 2010-04-09
Have you let it sit, while it was appearing frozen? How long?

---

### Post by Rocket2DMn on 2010-04-09
I saw this just a few minutes ago in Lucid, though the efffects did change.  I killed the frozen window using xkill from terminal.

---

### Post by infestor on 2010-04-10
> **Rocket2DMn said:**
> I saw this just a few minutes ago in Lucid, though the efffects did change.  I killed the frozen window using xkill from terminal.

so lemme get this right: you used xkill to kill the frozen appearance settings window and voila! it was set to extra or normal? i tried that but did not work for me. settings are always back to normal. i am using lucid too.

---

### Post by Rocket2DMn on 2010-04-10
> **infestor said:**
> so lemme get this right: you used xkill to kill the frozen appearance settings window and voila! it was set to extra or normal? i tried that but did not work for me. settings are always back to normal. i am using lucid too.

Yes, that is correct.  I selected the change I wanted, the window popped up asking if I wanted to keep the changes.  I tried to click Keep Settings but it wouldn't close.  At that point I used xkill to close the preferences window.

---

### Post by infestor on 2010-04-10
> **Rocket2DMn said:**
> Yes, that is correct.  I selected the change I wanted, the window popped up asking if I wanted to keep the changes.  I tried to click Keep Settings but it wouldn't close.  At that point I used xkill to close the preferences window.

that doesnt work for me...i will have to wait for an update

---

### Post by rejven on 2010-04-11
same problem
:(

---

### Post by krige on 2010-04-15
Try running:
```
sudo apt-get install compiz
```

---

### Post by ryandavis33 on 2010-04-15
i would bet you dont have the graphics drivers...my laptop has the same froblem:popcorn:

---

### Post by infestor on 2010-04-15
after running a new partial upgrade the problem solved! hallelujah!

---

### Post by johnnyslogan on 2011-01-30
```
sudo apt-get install compiz
```

Did it for me - could select normal under appearance, but the setting wasn't remembered. Above code fixed it. And it all - by the way - began when I installed nvidia-drivers on my intel-graphics system by accident. That meant, I lost opengl. Got it fixed by completely removing everything nvidia. 

Regards,
Jakob

---

