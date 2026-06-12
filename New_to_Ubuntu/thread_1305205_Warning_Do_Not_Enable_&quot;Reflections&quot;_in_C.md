---
title: "Warning: Do Not Enable &quot;Reflections&quot; in Compiz - GM965"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by asuastrophysics on 2009-10-29
**This is a warning for all Ubuntu users who have the Intel GM965 Chipset**

Do not enable "reflections" under "animations" in CCSM. You will not be able to log in again. 

To remedy this problem, you must delete your compiz configuration file. Unfortunately for me, I was not aware that this was a possibility, and I had to manually transfer all my files into a new username.

[COLOR="Red"]To fix compiz if you did enable "reflections":[/COLOR]
(Issue this from either the shell or from another user account with root privileges)
```
rm -r /home/username/.compiz
```

**Replace "username" with your username. Hit ENTER, and log back in. This should fix the problem.

Cheers! :popcorn:

---

### Post by ChappyHappy on 2009-11-12
Does this matter with which version of Ubuntu?
i just tried it with 9.10 and it crashed on me.

Any work around for this?

Ummm...for future reference...should I start new thread or post in existing thread that is marked as solved?

---

### Post by asuastrophysics on 2009-11-12
> **ChappyHappy said:**
> Does this matter with which version of Ubuntu?
i just tried it with 9.10 and it crashed on me.

Any work around for this?

Ummm...for future reference...should I start new thread or post in existing thread that is marked as solved?

9.10 is the version it crashed on with me too. You can post in here, it's cool. :)

---

### Post by coldReactive on 2009-11-12
I'm glad I run nvidia then. ;)

---

### Post by dejournett on 2010-01-08
So there's no way i can keep my existing prefs? i got ubuntu just for compiz... and now i gotta re-do it?

---

### Post by asuastrophysics on 2010-01-17
> **dejournett said:**
> So there's no way i can keep my existing prefs? i got ubuntu just for compiz... and now i gotta re-do it?

only this once. because you enabled reflections, and your hardware is incapable of displaying them, you will have inadvertently borked your compiz settings. 

however, if you wish to make a backup copy of your compiz settings, you can try this:
```
cp -r /home/username/.compiz /home/username/.compiz.backup
rm -r /home/username/.compiz
```

then, later you can go back and compare the old and new folders, and restore the changes you wanted to keep.

---

