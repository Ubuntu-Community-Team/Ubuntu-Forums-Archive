---
title: "Ubuntu Netbook Edition home screen gone"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by NeverSage on 2010-04-30
I'm running 10.04 Netbook edition.  I've found forum threads about this issue but I haven't found one that had a solution.  Randomly my home screen (favorites, settings, programs, accessories, etc) disappears and I'm left with the default background only.  This happened twice today.  I wouldn't mind that much if I only knew the terminal command to restart the home screen.  Does anyone know what I should try?  Thanks!

---

### Post by h1ll39 on 2010-07-09
I'm having the same issue. help would be awesome.

---

### Post by Paqman on 2010-07-09
Hit Alt-F2 and try:
```
netbook-launcher
```

If that doesn't work, open up a terminal and have a look at:
```
man netbook-launcher
```
to see if there's some clues.

---

### Post by h1ll39 on 2010-07-09
Thanks :)

---

### Post by rubyji on 2011-10-22
Thanks, Paqman. I just had this issue come up out of the blue today. 

I tried running netbook-launcher and nothing happened. When I run the man command, I get some documentation, but since it has no command-line options, I don't what else I can do.

---

