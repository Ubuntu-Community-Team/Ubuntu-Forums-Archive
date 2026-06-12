---
title: "graphicsmagick visual directory"
date: 2011-04-22
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2011-04-22
Hi Everyone,

I've been playing with GraphicsMagick and thought it would be kind of cool to use the visual directory feature.

[http://www.graphicsmagick.org/FAQ.html#what-are-visual-image-directories-how-do-i-use-them]("http://www.graphicsmagick.org/FAQ.html#what-are-visual-image-directories-how-do-i-use-them")

But when I run the command 
```

gm montage *.jpg directory.vid

```

or

```

gm convert 'vid:*.jpg' directory.vid

```

I get this:

```

gm montage: No encode delegate for this image format (directory.vid) [No such file or directory]

```

I'm running 
I don't know what that means or how to fix it. 

Any ideas?

---

### Post by GrouchyGaijin on 2011-04-23
bump

---

### Post by Locke_99GS on 2011-04-23
Instead of .vid, give it a proper file extension such as .png.

```

gm montage *.jpg directory.png

```

---

### Post by GrouchyGaijin on 2011-04-23
> **Locke_99GS said:**
> Instead of .vid, give it a proper file extension such as .png.

```

gm montage *.jpg directory.png

```

Thanks that solved the initial problem.  It seems pretty buggy though.  I guess I'll just use GM for resizing batches of images and to manipulate images in scripts.  I'll use something else like Mirage for actually viewing the images.

---

