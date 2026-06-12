---
title: "Power Management Daemon"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by mesmith on 2009-04-20
I'm running a Dell desktop with Pentium 4 dual processor and 1gb memory.  I run the system with hd and display always on.  I never use suspend or hibernate.  Can I safe uncheck the Power Management Daemon in Autostarted apps or will I break something?

Thanks.

---

### Post by sdennie on 2009-04-20
If it's an option, it's probably "safe" to uncheck it.  However, I'm not sure what you are trying to accomplish by doing so.  acpid uses almost no resources and it's probably controlling things you didn't realize it's controlling.

---

### Post by mesmith on 2009-04-20
The reason for my question is that once every 8 boots, or so, I get a hang.  It seems like the last text is something about checking battery status.  I am trying to eliminate the hangs.  The hang consists of a black screen with lots of disk activity, then nothing.  A reboot always solves the hang.

---

### Post by sdennie on 2009-04-20
Then I would certainly try it.  It's not going to do anything horrible to your machine and if your theory doesn't pan out, it's just a matter of turning it back on.

---

