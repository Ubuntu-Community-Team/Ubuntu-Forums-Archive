---
title: "error on boot"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by Lewnick on 2009-02-07
I am brand new to Ubuntu. I just bought a new Dell laptop and it came with the Ubuntu, so I am learning as I go. Here is my latest issue;

When I attempt to boot the system I get this error

Traceback (most recent call last)
File "/usr/sbin/oem-config-dm", line 140, in <module>
sys.exit(dm.run(*sys.argv[3:]))
raise X StartupError, "X server failed to start after 60 seconds

---

### Post by itix on 2009-02-09
Ouch... That means the graphical "engine" cannot start.

Did you by any chance do something to cause this. Has it worked at all??

---

