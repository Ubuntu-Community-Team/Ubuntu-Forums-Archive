---
title: "Stop suspending/sleeping while connected using SSH"
date: 2011-06-13
forum: New to Ubuntu
---

### Post by niranjan_rao on 2011-06-13
I have a ubuntu desktop 10.10 to which I would like to SSH. This part works. However the desktop is set to suspend/sleep after ten minutes of inactivity. It seems like ssh is not counted as being active and machine suspends itself.

Is there any way I can configure the desktop so that it won't suspend/sleep while I am connected using SSH.

My normal pattern is to use wake up on lan to wakeup the desktop before I start using it. Do my work using ssh and then let it sleep.All the things work perfectly except the part that ssh hangs after ten minutes as server goes to sleep.

---

### Post by drunk.esteban on 2011-08-06
I'm having the same problem.

Particularly annoying when you wake-on-lan to do an apt-get update && apt-get upgrade ... laptop falls asleep before the process finishes, even when using screen this causes problems

---

