---
title: "Bug in my upstart script?"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by kraen on 2009-02-05
Hey,
I'm pretty new to the more server aspects of ubuntu, and need some help with a script I've written for the upstart daemon. Script as follows.

```
#Liquidsoap setup

start on startup

respawn
exec liquidsoap /path/to/file/liquidsoapconfig.liq
```

The command is correct, although obviously the path info has been changed. Now unless I'm reading the examples completely wrong this should start when the computer starts (and before anyone logs in?) and automatically restart the process if it terminates. Is that correct?

Thanks in advance.

I also know this is like dozens of other threads about upstart, but I believe the issue is with my script so felt it worth posting a new topic.

---

