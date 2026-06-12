---
title: "Restart a process when it crashes?"
date: 2010-03-01
forum: New to Ubuntu
---

### Post by TurnOfTide on 2010-03-01
How can i restart a process after it has exited. Say a program runs, crashes or just completes normally, i want to run it again.

---

### Post by patchwork on 2010-03-01
If you want it to restart automatically (i.e., not on-demand) you can use the program monit.  monit will check the specifed processes at a specified time interval and attempt to restart the process if it ends or fails.

---

