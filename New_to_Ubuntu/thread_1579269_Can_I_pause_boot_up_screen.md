---
title: "Can I pause boot up screen?"
date: 2010-09-21
forum: New to Ubuntu
---

### Post by held7over on 2010-09-21
Ubuntu 10.04  There are some complaint messages being flashed to the screen during boot up on my IBM Thinkpad 600e, but they are erased too fast for me to read them. Is there a key combination or something that would let me pause the bootup screen so I can read the messages?

Thanks! :)

---

### Post by sandyd on 2010-09-21
> **held7over said:**
> Ubuntu 10.04  There are some complaint messages being flashed to the screen during boot up on my IBM Thinkpad 600e, but they are erased too fast for me to read them. Is there a key combination or something that would let me pause the bootup screen so I can read the messages?

Thanks! :)
their in the system log.
check /var/log/syslog and /var/log/kern.log.
also boot.log

---

### Post by drs305 on 2010-09-21
> **sandyd said:**
> their in the system log.
check /var/log/syslog and /var/log/kern.log.
also boot.log

Hint to OP: You can easily access those files via System, Administration, Log File Viewer.  If you can catch a keyword you can use CTRL-f to search the log.

---

### Post by Paul820 on 2010-09-21
Or go to System->Administration->Log File Viewer, on the left hand side look for 'syslog' and click the little arrow, look for the date of the log you want to view.

EDIT: I type too slow, drs305 beat me to it!

---

### Post by held7over on 2010-09-21
Thanks! That's great!

---

