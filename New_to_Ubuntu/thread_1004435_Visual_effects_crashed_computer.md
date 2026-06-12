---
title: "Visual effects crashed computer"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by tegnoto89 on 2008-12-07
I went to apply some enhanced visual effects, and apparently my hardware couldn't handle it.  I got a black screen, had to shut down.  Now when I try to log in I get a black screen and I can't get to the system options to change it.

HELP!!!

---

### Post by tegnoto89 on 2008-12-07
I can't access my desktop at all right now, so any help anybody could give would be MUCH appreciated.

---

### Post by tegnoto89 on 2008-12-07
can't anyone offer me aything??

---

### Post by neerajvm on 2008-12-07
This is just happened to me couple of days ago. This is what I did. Either boot into recovery mode from grub, or choose failsafe terminal from sessions while entering username(GDM screen). Then

[CODE]

~$cd .gconf/apps/compiz
~$rm * -r

/[CODE]


Essentially, we're just deleting the configuration file for compiz. So, it gets reset to default state. Now reboot system and it should be up and running again!

---

