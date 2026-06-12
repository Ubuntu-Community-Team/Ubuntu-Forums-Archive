---
title: "I've done something really bad  please help"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by enri2 on 2009-03-28
when i restarted my pc  , the windows don't have title bars   and they start  in maximized mode.  the last thing I did  is installed ubuntu studio and i messed with compiz settings

---

### Post by Temposs on 2009-03-28
Press Alt+F2 and type:

```
metacity --replace
```

That will disable compiz and let you work with a sane system while you fix compiz.

---

### Post by mcduck on 2009-03-28
For starters, press Alt-F2 (or open a terminal) and run "metacity --replace". That should at least get you a working system without Compiz. Much nicer to fix Compiz setting that way. :)

---

### Post by drs305 on 2009-03-28
One thing you can try to stil run compiz is to open the Compiz Configuration Settings Manager > Effects and tick 'Window Decoration'.

If you don't have the Config Settings manager installed:
```
sudo apt-get install compizconfig-settings-manager
```

To run it, "ccsm" or System, Preferences, CompizConfig Settings Manager.

Note: To restart compiz:
```

compiz --replace

```
;-)

---

