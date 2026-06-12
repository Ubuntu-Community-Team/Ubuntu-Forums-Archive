---
title: "Tomboy notes are not restoring"
date: 2009-12-09
forum: New to Ubuntu
---

### Post by rkakkar on 2009-12-09
I saved the notes from the ~/.tomboy folder on another computer and when i try to paste them here, the notes aren't showing up! any other way to restore them?

---

### Post by plucky on 2009-12-09
> **rkakkar said:**
> I saved the notes from the ~/.tomboy folder on another computer and when i try to paste them here, the notes aren't showing up! any other way to restore them?

If you are running Karmic,the tomboy folder is located in ```
~/.local/share/tomboy/
``` Copy the notes there and then log out and log back in and they should appear.

If you aren't running Karmic,what are you running?


Good Luck

---

### Post by jimmy the saint on 2009-12-09
After you copy them into the correct folder, restart the system.  I had the same issue last year.  Spent an hour trying to figure it out, gave up, shut down.  When I came back BAM, there they were.  I am sure there is a way to do it without a restart, but on a non-server, non-production system, sometimes the simplest thing to do is a simple restart.

---

### Post by sharm on 2009-12-10
You can also just restart Tomboy (if you use it as a panel applet, remove it from and then re-add it to your panel).

---

### Post by rkakkar on 2009-12-12
> **plucky said:**
> If you are running Karmic,the tomboy folder is located in ```
~/.local/share/tomboy/
``` Copy the notes there and then log out and log back in and they should appear.

If you aren't running Karmic,what are you running?


Good Luck

this worked!! thanks :)

---

