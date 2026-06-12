---
title: "imagemagick"
date: 2009-10-28
forum: New to Ubuntu
---

### Post by ub9876 on 2009-10-28
I got this installed from Synaptic.. but its not showing up in Graphics or any of the other applications..  where did it go and how to get it running??????????
9.04

---

### Post by dominiquec on 2009-10-28
It's a collection of command line utilities for manipulating graphics, not a graphical application in itself.

I find it quite useful, for example, resizing all the pictures in a folder is just one command:

```
mogrify -scale 50% *.jpg
```

To find out more about what it does, do ```
man ImageMagick
```.

---

