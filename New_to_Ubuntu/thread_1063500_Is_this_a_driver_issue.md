---
title: "Is this a driver issue???"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by dniezby on 2009-02-07
I was just trying to play the 3D version of the chess game that comes with Ubuntu and this is the error I get.

No Python OpenGL support
No Python GTKGLExt support


Is this a driver issue or something that I can't fix without replacing the graphics card.

---

### Post by handydan918 on 2009-02-07
Could be either, what is your graphics card?

Output of ```
lspci | grep -i vga
```

---

### Post by dniezby on 2009-02-08
I assume that you wanted me to enter this in the terminal?

This is was came back
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series

---

### Post by jimrz on 2009-02-08
I think this has been a bug in the default chess for some time now.
It does not work with the ati card in my laptop, either.
I use Dream Chess, which can be installed via synaptic. It works well and is a formidable opponent ;)

---

