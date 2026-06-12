---
title: "Error __init__.py in many programs"
date: 2010-02-02
forum: New to Ubuntu
---

### Post by andre.maldonado on 2010-02-02
Hi, 

I'm getting errors like this above in many programs, like: Software Sources, Bazaar, Hardware drivers, Main menu, and others. What can I do to fix it? I've tried a lot of things and nothing solved the problem.

```
gksu --desktop /usr/share/applications/software-properties.desktop /usr/bin/software-properties-gtk
Traceback (most recent call last):  File "/usr/bin/software-properties-gtk", line 27, in <module>
    import gtk
  File "/usr/lib/pymodules/python2.6/gtk-2.0/gtk/__init__.py", line 30, in <module>
    import gobject as _gobject
  File "/usr/lib/pymodules/python2.6/gtk-2.0/gobject/__init__.py", line 26, in <module>
    from glib import spawn_async, idle_add, timeout_add, timeout_add_seconds, \
  File "/usr/lib/pymodules/python2.6/gtk-2.0/glib/__init__.py", line 22, in <module>
    from glib._glib import *
ImportError: libffi.so.5: cannot open shared object file: No such file or directory
```
Thank's

---

### Post by lotharmat on 2010-02-02
The last time I had an error 'like' this - Was in Ubuntu tweak.

Rebooting the machine cured it.. I know.. It is sooooo Windows; but have you tried this?

---

### Post by Flimm on 2010-02-02
Looks like libffi.so.5 is missing from your system. I did a search for it on mine and got:```
$ dpkg -S libffi.so
libffi5: /usr/lib/libffi.so.5
libffi5: /usr/lib/libffi.so.5.0.8
libffi-dev: /usr/lib/libffi.so
$
```

So my advice would be to reinstall libffi5:```
sudo apt-get install --reinstall libffi5
```

---

### Post by andre.maldonado on 2010-02-02
> **Flimm said:**
> Looks like libffi.so.5 is missing from your system. I did a search for it on mine and got:```
$ dpkg -S libffi.so
libffi5: /usr/lib/libffi.so.5
libffi5: /usr/lib/libffi.so.5.0.8
libffi-dev: /usr/lib/libffi.so
$
```So my advice would be to reinstall libffi5:```
sudo apt-get install --reinstall libffi5
```

Flimm, I did what you said and solved my problems.

Thank's a lot!!!

---

