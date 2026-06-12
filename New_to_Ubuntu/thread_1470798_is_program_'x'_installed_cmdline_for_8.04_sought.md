---
title: "is program 'x' installed? cmdline for 8.04 sought"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by bobox on 2010-05-03
I'm a newbie working my way into a new installation of the Ubuntu 8.04-based Bio-Linux from NEBC ([http://nebc.nerc.ac.uk/nebc/support/training/course-notes/past-notes/intro-bl5](http://nebc.nerc.ac.uk/nebc/support/training/course-notes/past-notes/intro-bl5))

Is there a commandline query I can run to find a particular program/whether it's installed or not?  I thought that 'whereis' would do this, but have just learnt this isn't the case; it returns only for commands rather than programs

TIA

bbx

---

### Post by dv3500ea on 2010-05-03
```
dpkg --get-selections program
```

---

