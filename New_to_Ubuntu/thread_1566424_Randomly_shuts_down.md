---
title: "Randomly shuts down"
date: 2010-09-02
forum: New to Ubuntu
---

### Post by DarrenMR415 on 2010-09-02
Laptop randomly dies.  Its almost exactly like the battery died.  Only when I restart it claims the battery is 100% or close to it.  And Im just about always plugged in.  Is there anything I can look up that will give me a log, or anything that I can have running that will log if it happens again?

---

### Post by ibizatunes on 2010-09-02
Well, may be have a look in /var/log/, in particular syslog.0 file.
less /var/log
or tail -50 /var/log/syslog.0 and post that and that will give you some clue as to what your computer is doing before it shutdown

---

### Post by DarrenMR415 on 2010-09-02
Did a partial dismantle.  There was a furball caught in my fan.  So I think I may have been over-heating and the system was shutting down to protect itself.  This shutdown had happened a few times last week so I dont know if its the same thing or not.

---

