---
title: "Can't track down why laptop won't suspend / hibernate"
date: 2010-07-07
forum: New to Ubuntu
---

### Post by vysotsky on 2010-07-07
Since upgrading to 10.04 LTS 64-bit, my HP Pavilion dv4t-1000 laptop has hung when I try to suspend the system: everything seems to go well at first, the screen blinks off for a moment, and then suddenly turns back on with a blank screen and the computer hangs and is totally unresponsive.

I've looked through the system logs, but I'm having trouble tracking down the problem.  I've looked at the syslog and the pm-suspend log, and neither of them seem to show any problem.  (I'm seeing lots of messages that end with "success" before "performing suspend" and then nothing until I restart the machine.)  

Can anyone tell me how to proceed?  What should I look for that might cause the problem?

I've had no problem suspending and hibernating on previous versions of Ubuntu, so I'm hoping this won't be too complicated to fix once I figure out what's going wrong.  I'd be happy to attach logfiles if anyone can tell me which ones might be relevant for diagnosing the problem.

---

### Post by cariboo on 2010-07-08
I ran into something similar on my Compaq mini 110. I get the same symptoms if I leave the AC cord plugged in. Could this be your problem?

---

### Post by vysotsky on 2010-07-08
It certainly could be the same problem, since I can't suspend the computer whether it's plugged in or on battery power.  Did you find a solution?

---

