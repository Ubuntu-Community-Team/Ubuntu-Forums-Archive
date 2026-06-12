---
title: "Renpy crashes"
date: 2009-11-28
forum: New to Ubuntu
---

### Post by LunaticHiatus on 2009-11-28
when running renpy in terminal. I get:

/usr/share/games/renpy/renpy/parser.py:29: DeprecationWarning: the sets module is deprecated
  import sets
/usr/share/games/renpy/renpy/script.py:31: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import md5
Fatal Python error: (pygame parachute) Segmentation Fault
Aborted

how do I file a bug report?

---

### Post by cariboo on 2009-11-28
You can report a bug, by pressing Alt-F2 and typing:

```
ubuntu-bug <packagename>
```

in this case substitute renpy for <packagename>

You may be asked to create a [Launchpad]("https://launchpad.net/") account.

---

