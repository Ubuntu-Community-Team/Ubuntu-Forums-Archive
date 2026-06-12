---
title: "can't get awn-manager to run"
date: 2010-02-01
forum: New to Ubuntu
---

### Post by warthogism on 2010-02-01
i did a search and found some people with the same problem, but what worked for them did not for me...

```
wheeze@wheezeeepc:~$ awn-manager
Traceback (most recent call last):
  File "/usr/bin/awn-manager", line 220, in <module>
    awnmanager = AwnManager()
  File "/usr/bin/awn-manager", line 136, in __init__
    self.prefManager = awnPreferences(self.wTree)
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 109, in __init__
    self.setup_look(defs.BAR, defs.BAR_ANGLE, self.wTree.get_widget("look"))
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 363, in setup_look
    self.changed_look(dropdown)
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 377, in changed_look
    self.reload_look(0, dropdown)
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 368, in reload_look
    if self.client.get_int(defs.BAR, defs.BAR_ANGLE) == 0:
glib.GError: Type mismatch: Expected `int' got `float' for key /apps/avant-window-navigator/bar/bar_angle
```

I have already run awn once. i've tried opening it through the system>preferences.  I've also tried by right-clicking on the dock itself.  Neither appears to do anything.  then I got idea to use the terminal as you can see, but the return means nothing to me...i've also tried several rounds of complete removal and installations.

any ideas?  tia.

---

### Post by redbook4574 on 2010-02-01
Try cairo-dock instead, runs perfectly, i also had many problems with awn,
although I'm sure many will shout me down now but I have a system which makes windows 7 users spit feathers.

---

