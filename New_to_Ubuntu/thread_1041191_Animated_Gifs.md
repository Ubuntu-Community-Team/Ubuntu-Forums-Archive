---
title: "Animated Gifs"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by Haruki-kun on 2009-01-16
I usually open animated Gifs on FireFox, but is there any make the image viewes open them and actually see the animation without using FireFox?

---

### Post by kaibob on 2009-01-16
> **Haruki-kun said:**
> I usually open animated Gifs on FireFox, but is there any make the image viewes open them and actually see the animation without using FireFox?

The display utility, which is a part of the imagemagick suite, will view animated gifs. If you have imagemagick installed, just type the following in a terminal window:

```
display filename.gif
```

If I remember correctly, gthumb, which is in the repo's, will also display animated gifs.

---

### Post by anewguy on 2009-01-16
Or just use the GIMP and look at the layers (each layer part of the animation).

dave :)

---

