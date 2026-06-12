---
title: "Panel does noes appear on start-up"
date: 2010-12-04
forum: New to Ubuntu
---

### Post by Peter.Paul on 2010-12-04
Hello,
I installed ubuntu and it works perfectly except for one thing. Sometimes if I boot my system, the panel bar at the very top of the screen does not appear. 

Do you know, how to solve the problem?

---

### Post by nunkstop on 2010-12-04
re-install to fix it! :D

---

### Post by wilee-nilee on 2010-12-04
> **Peter.Paul said:**
> Hello,
I installed ubuntu and it works perfectly except for one thing. Sometimes if I boot my system, the panel bar at the very top of the screen does not appear. 

Do you know, how to solve the problem?


Which Ubuntu distro is it?

---

### Post by uriel1998 on 2010-12-04
> **Peter.Paul said:**
> Hello,
I installed ubuntu and it works perfectly except for one thing. Sometimes if I boot my system, the panel bar at the very top of the screen does not appear. 

Do you know, how to solve the problem?

Do all your panels not appear, or just one?  This is a bit of an extreme work-around, but it helped me when the bits of the Gnome panel moved around randomly (on 10.04):

At the console, type:
```
gconftool-2 --dump /apps/panel > ~/panel_backup.xml
```

(You can put whatever directory you like - that has it going to the home directory.  You will probably want to put a full, explicit directory name there.)  That backs up all of your panels.  Then I had this running as a startup script:
```
#!/bin/bash
gconftool-2 --load ~/panel_backup.xml
killall gnome-panel
gnome-panel &
```

It's a bit of a hack, but it worked for me.

---

