---
title: "error when opening google sketchup in ubuntu 9.10"
date: 2010-04-16
forum: New to Ubuntu
---

### Post by domack on 2010-04-16
When opening google sketchup in 9.10 the following error message comes up:

" Sketchup was unable to initialize OpenGL. Make sure the correct driver for graphics card is installed. Error: Choose Pixel Format failed. "

Thanks for any suggestions to fix this.
D

---

### Post by kellemes on 2010-04-16
> **domack said:**
> When opening google sketchup in 9.10 the following error message comes up:

" Sketchup was unable to initialize OpenGL. Make sure the correct driver for graphics card is installed. Error: Choose Pixel Format failed. "
Thanks for any suggestions to fix this.
D

How are you opening Sketchup?
I thought there was no version avaliable for Linux..

Edit:
WineHQ shows this is a [bug]("http://bugs.winehq.org/show_bug.cgi?id=14045").
Seems to be fixed like so..

```
bug 14045: If you get the error "SketchUp was unable to
initialize OpenGL!], run regedit, open
HKEY_CURRENT_USER\Software\Google\SketchUp6\GLConfig\Display,
and change HW_OK to 1.
```

---

### Post by domack on 2010-04-16
with wine you can run Windows programs if all goes well.

[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

---

