---
title: "Latest update broke DockBarX (0.39.6)"
date: 2010-07-19
forum: New to Ubuntu
---

### Post by 416inversed on 2010-07-19
The latest update to Dockbar X (0.39.6) broke it on my system. I'm getting the whole "encountered a problem loading" "delete/don't delete" window.

I've removed from panel & re-added. I've purged & reinstalled. I've rebooted. I followed a different thread about installing python-keyring, but nothing seems to work.

I've been alt-tab'ing as my app switcher all morning, which may be more efficient, but not as pretty.

So, any ideas?

---

### Post by zehjotkah on 2010-07-19
I have the same problem, even reinstalled my whole system, but dockbarx remains broken. 
hoping for a solution, too...

---

### Post by zehjotkah on 2010-07-19
Okay, found the fix:
you have to install zeitgeist from the zeitgeist ppa... worked for me...

```
sudo add-apt-repository ppa:zeitgeist/ppa && sudo apt-get update
sudo apt-get install libgtk2.0-0 libx11-6 libxcomposite1 zeitgeist
```

> Zeitgeist powers those nice "Recent",  "Most used" and "Related"  submenus when you right click. You won't get them by installing the  version of zeitgeist that is in the lucid repository, you need the ppa  version. It is a bug that you had to install zeitgeist. It is supposed  to be optional and in x.0.39.6 it is again.

Source: [https://bugs.launchpad.net/dockbar/+bug/606568](https://bugs.launchpad.net/dockbar/+bug/606568)

---

### Post by M7S on 2010-07-19
If you have a problem in x.0.39.6 please run dockbarx in window and post the errors.

```
dockbarx_factory.py run-in-window
```

If you are running x.0.39.5 or x.0.39.5-1 you probably suffer from the bug zehjotkah describes.

---

### Post by Foxcow on 2010-07-20
I'm curious to see if this gets resolved as well because I really like DockbarX

---

### Post by rCXer on 2010-07-20
Make sure you post this in the comments [here]("http://gnome-look.org/content/show.php?content=101604"). DockbarX's developer, M7S, reads the comments all the time.

---

### Post by M7S on 2010-07-20
Hello, I'm reading this thread as well. :)

---

### Post by M7S on 2010-07-20
If it is that zeitgeist bug, it is resolved already, just wait for reeve to package the release and it will show up in the ppa. If you have installed dockbarx from the source at gnome-look.org, please run dockbarx in window (see my previous post) and post the error message!

---

### Post by leonardo_neo on 2010-07-21
> **M7S said:**
> If it is that zeitgeist bug, it is resolved already, just wait for reeve to package the release and it will show up in the ppa. If you have installed dockbarx from the source at gnome-look.org, please run dockbarx in window (see my previous post) and post the error message!
> :~$ dockbarx_factory.py run-in-window

** (dockbarx_factory.py:3327): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (dockbarx_factory.py:3327): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (dockbarx_factory.py:3327): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
Traceback (most recent call last):
  File "/usr/bin/dockbarx_factory.py", line 26, in <module>
    import dockbarx.dockbar
  File "/usr/lib/python2.6/dockbarx/dockbar.py", line 36, in <module>
    from groupbutton import *
  File "/usr/lib/python2.6/dockbarx/groupbutton.py", line 39, in <module>
    import zg
  File "/usr/lib/python2.6/dockbarx/zg.py", line 40, in <module>
    result_type=datamodel.ResultType.MostRecentSubjects,
NameError: name 'datamodel' is not defined


This is the output in my system.

**Update: I updated on 22nd July 2010, the updates provided by the update manager. There was also an update for DockbarX, and that fixed my problem. Thanks.**

---

### Post by Nencio on 2010-07-22
I had the same problem as above.
It got fixed in the new version (0.39.1.1 from the ppa).

---

