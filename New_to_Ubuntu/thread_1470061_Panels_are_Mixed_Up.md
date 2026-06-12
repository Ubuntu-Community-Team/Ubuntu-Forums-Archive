---
title: "Panels are Mixed Up"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by EnigmaticCoder on 2010-05-02
After installing Ubuntu from scratch, the display had to run in reduced settings and a lower resolution. I fixed that problem, but now the panels are mixed up i.e. the trash can icon is not at the bottom right corner.  Instead, the workspace icon is there, and the trash can icon is closer to the middle of the panel.

Is there a way to fix this or reset the panels to their default setting?

---

### Post by compiz addict on 2010-05-02
Right click on a panel icon, and make sure "Lock to Panel" is NOT checked (if it is un-check it), and then click "Move" and drag the mouse to the place you want. Also, to get back missing icons, right click on an empty space on the panel, click "Add to Panel..." and browse the available icons.

Hope this helps.

---

### Post by Kafubie on 2010-05-02
For some reason. Once in a while my icons get scattered even though I put almost all of my applets on "lock".  Does anybody know about this bug?:P

---

### Post by SnickerSnack on 2010-05-02
> **Kafubie said:**
> For some reason. Once in a while my icons get scattered even though I put almost all of my applets on "lock".  Does anybody know about this bug?:P

So do mine.

I think it only happens when I shutdown/restart, but not when I suspend.

---

### Post by tom.swartz07 on 2010-05-02
The easiest way to revert the panels to the original setting (the one that you have right after a fresh install) is to remove all of the configuration files.

Please note that this will delete the files, so if you think you might want them, back them up first....

```
rm -r ~/.gconf/apps/panel
```
Logout/in and you should be all set!

---

### Post by compiz addict on 2010-05-02
Just a random question that's sorta related,
will rm -r ~/.gconf/* reset everything?

---

### Post by EnigmaticCoder on 2010-05-02
Thanks everyone. Unticking lock to panel and moving the icons did the trick.

---

### Post by tom.swartz07 on 2010-05-02
> **compiz addict said:**
> Just a random question that's sorta related,
will rm -r ~/.gconf/* reset everything?

Yepper

---

