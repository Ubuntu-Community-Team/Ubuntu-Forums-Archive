---
title: "quick link button to turn off the computer"
date: 2010-02-21
forum: New to Ubuntu
---

### Post by fwin on 2010-02-21
Hi everyone, i was uninstalling empathy and skype from my computer and i dont know what i did that i made the quick link button on the upper right corner (the one where you choose if you want to switch users, logout, turnoff, restart) disappear. 

Please help !  :confused:

---

### Post by mikewhatever on 2010-02-21
I suspect that somehow, the indicator-applet-session got removed. Try reinstalling the package.

sudo apt-get install indicator-applet-session

---

### Post by fwin on 2010-02-21
mikewhatever,

thanks for the help, that solved the problem, but i just figured out that i have another one, the volume and network indicator are also gone, any hints?

thanks

---

### Post by fwin on 2010-02-21
never mind, i just found it under :

add to panel --> notification area

thanks for everything:P

---

