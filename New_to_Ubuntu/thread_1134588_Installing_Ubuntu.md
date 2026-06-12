---
title: "Installing Ubuntu"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by newbie316 on 2009-04-23
I have a used PC that I did a WipeDisk on and installed Ubuntu 8.10. Now when I try to boot it up, it asks for the user name and password, but then hangs at the tan background desktop. I originally had on 512MG ram but have upgraded that to 2G. Still, same problem.  Any ideas?  Thank you!!!

---

### Post by MuddBuddha on 2009-04-23
Did the LIVE CD work okay before installing?  That may indicate a problem with the PC architecture with Ubuntu.

If all else fails, I would try another clean install.

---

### Post by ugriffin on 2009-04-23
I suggest you specify more about what happens....

Still... I think your ubuntu-desktop packages got corrupted. So I suggest you resintall ubuntu-desktop. It's not a full system restart... and I've fixed tons of KDE installations this way. Give it a try.

WARNING: WILL TAKE A LONG TIME, AND IT'S PRETTY MUCH GONNA PURGE HALF YOUR SYSTEM.

```

sudo aptitude purge ubuntu-desktop

```
when it's done:
```

sudo apt-get install ubuntu-desktop

```

EDIT: You need internet for this to work.

---

