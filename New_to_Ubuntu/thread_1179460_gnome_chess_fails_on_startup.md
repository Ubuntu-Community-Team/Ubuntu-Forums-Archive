---
title: "gnome chess fails on startup"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by k_squired on 2009-06-05
Yes the error message says something like 

File "/usr/lib/python2.6/dist-packages/OpenGL/arrays/nones.py", line 32, in zeros
    raise TypeError( """Can't create NULL pointer filled with values""" )
TypeError: ("Can't create NULL pointer filled with values", 'Failure in cConverter <OpenGL.converters.SizedOutput object at 0x9e95c6c>', [GL_TEXTURE_2D], 1, <OpenGL.wrapper.glGetIntegerv object at 0x9ea4aac>)


Uh, thanks for any help.

---

### Post by jonobr on 2009-06-05
This appears to be a known open issue in 9.04 with no solution as of yet

See [This]("https://bugs.launchpad.net/gnome-games/+bug/351142")

---

