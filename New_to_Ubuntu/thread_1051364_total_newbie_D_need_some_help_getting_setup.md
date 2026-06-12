---
title: "total newbie :D need some help getting setup"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by zigzagff17 on 2009-01-26
Ok, I got a new HD for my laptop, windows didn't want to cooperate, so i put in the new Ubuntu cd and BAM, it installed and everything seems great ... but I'm pretty much lost, I have wireless in my house and my wireless button on my laptop is orange, should be blue when its on(yeah i turned it on).  So basically i need how get online so i can learn more

Thanks

Zack

---

### Post by RomeReactor on 2009-01-26
Hi. We need to know more about your wireless card. Please open a terminal (Applications->Accessories->Terminal) and paste this:
```
lspci -nn | grep Ethernet
```
and post back the output.

---

### Post by zigzagff17 on 2009-01-26
ths is what came out:

00:14.0Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269]
(rev a3)

---

### Post by Muffinabus on 2009-01-26
What version of Ubuntu did you install?

---

### Post by zigzagff17 on 2009-01-26
woohoo, i figured something out... i check the hardware devices and noticed i had to activate that driver .. did it, rebooted and it worked.

Thanks for the info, now it time for linux school

---

### Post by zigzagff17 on 2009-01-26
Ubuntu 8.10

---

### Post by Muffinabus on 2009-01-26
> **zigzagff17 said:**
> woohoo, i figured something out... i check the hardware devices and noticed i had to activate that driver .. did it, rebooted and it worked.

Thanks for the info, now it time for linux school

Hehe, good for you!  Enjoy!

---

### Post by RomeReactor on 2009-01-26
Glad you got it working!

---

