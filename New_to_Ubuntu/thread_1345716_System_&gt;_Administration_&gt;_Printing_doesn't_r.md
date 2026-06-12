---
title: "System &gt; Administration &gt; Printing doesn't run anything."
date: 2009-12-04
forum: New to Ubuntu
---

### Post by BioVirtual on 2009-12-04
System > Administration > Printing doesn't run anything.

When I want to print a PDF if I go to properties of my printer (from Adobe PDF Reader) and change any setting, everything gets closed when I press OK.

---

### Post by oldos2er on 2009-12-04
What make/model of printer? Can you run system-config-printer in a terminal and post the output here?

---

### Post by BioVirtual on 2009-12-06
Well, It's kinda disappointing I guess:

```

Traceback (most recent call last):
  File "/usr/share/system-config-printer/system-config-printer.py", line 30, in <module>
    from timedops import *
  File "/usr/share/system-config-printer/timedops.py", line 20, in <module>
    import gobject
ImportError: No module named gobject

```

---

