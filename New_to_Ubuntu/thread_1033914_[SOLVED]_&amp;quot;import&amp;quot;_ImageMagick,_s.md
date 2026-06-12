---
title: "[SOLVED] &amp;quot;import&amp;quot; ImageMagick, saving a fixed rectangle of screen?"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by linkmaster03 on 2009-01-07
I am using the 'import' command of ImageMagick, and I am trying to save a specified rectangle. I don't want to have the normal crosshair to drag an area of the screen, I just want to save a rectangle. I have read the man page and the website, and I can't figure out how. This is what I tried:

```
import -geometry 765x501-1023-658 test.png
```

EDIT: Yay, I solved it by using this:

```
import -window root -crop 765x501+257+142 test.png
```

(same geometry just written with +)

Hope this helps someone else solve their problem.

---

