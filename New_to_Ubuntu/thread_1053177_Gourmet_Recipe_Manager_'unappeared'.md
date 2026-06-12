---
title: "Gourmet Recipe Manager 'unappeared'"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2009-01-28
I use Gnome. This is Ibex. I used Applications - Add/Remove to install Gourmet Recipe Manager (REPO: universe). It asked for my p/w. Went through the install and there is neither an icon in the Applications (used to add a menu item: Other), then moved to Accessories. But the app didn't appear. Running 

gourmet

in a terminal brings up:

mark@Lexington-19:~$ gourmet
Traceback (most recent call last):
  File "/usr/bin/gourmet", line 13, in <module>
    from gourmet.OptionParser import *
  File "/usr/lib/python2.5/site-packages/gourmet/__init__.py", line 14, in <module>
    import keymanager
  File "/usr/lib/python2.5/site-packages/gourmet/keymanager.py", line 3, in <module>
    from defaults import langProperties as langProperties
ImportError: cannot import name langProperties


Anybody got a clue? I wrote the program's author about this. He asked me what language and location I was using. I answered: English and US. That's what Ibex found on install or what I selected on install. He hasn't written back.

---

