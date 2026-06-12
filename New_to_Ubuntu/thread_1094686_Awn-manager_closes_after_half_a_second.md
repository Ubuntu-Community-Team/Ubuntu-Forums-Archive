---
title: "Awn-manager closes after half a second"
date: 2009-03-12
forum: New to Ubuntu
---

### Post by joesmith1806 on 2009-03-12
when i try and start awn manager System> Preferences> Awn Manager it only opens for a fraction of a second and closes again when i try to run it in terminal is throws this message:

joe@joe-desktop:~$ awn-manager
/usr/share/avant-window-navigator/awn-manager/awnPreferences.py:242: DeprecationWarning: raising a string exception is deprecated
  raise "\nKey: "+key+" isn't set.\nRestarting AWN usually solves this issue\n"
Traceback (most recent call last):
  File "/usr/bin/awn-manager", line 200, in <module>
    awnmanager = AwnManager()
  File "/usr/bin/awn-manager", line 101, in __init__
    self.prefManager = awnPreferences(self.wTree)
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 150, in __init__
    self.setup_chooser(APP_ACTIVE_PNG, self.wTree.get_widget("activefilechooser"))
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 242, in setup_chooser
    raise "\nKey: "+key+" isn't set.\nRestarting AWN usually solves this issue\n"

Key: /apps/avant-window-navigator/app/active_png isn't set.
Restarting AWN usually solves this issue



if any one could shed some light that would be most appreciated!

---

### Post by joesmith1806 on 2009-03-12
Its ok i solved it. Turnes out i had to run the actual dock before i could run awn manager

---

