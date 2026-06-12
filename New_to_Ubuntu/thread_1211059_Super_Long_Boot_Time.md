---
title: "Super Long Boot Time"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by sum janus on 2009-07-12
Hi guys,

I'm having a problem with my fresh Ubuntu installation.  After I select "Ubuntu" from GRUB "Starting up..." appears, it takes about a minute and a half before the familiar Ubuntu logo shows up.  Every thirty seconds or so, a handful of lines of output shows up, but I don't understand it.

What can I do to diagnose, or solve, this problem?  Any help would be appreciated :).

Thanks!

---

### Post by s.fox on 2009-07-12
Hi,

Could you please post what these lines are?

Thanks,

-Silver Fox

---

### Post by ajgreeny on 2009-07-15
When you get to the grub menu next time choose your ubuntu and hit the E key, then the down key to the kernel line and hit the E key again.  Now scroll to the end of the line that appears with the right cursor key and delete the words **quiet splash**

Hit return and then the B key to boot, but for this time only in text mode, so you will see where the delay is.  Post back here and I'll see what I can suggest.

---

