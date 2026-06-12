---
title: "How do I find out what drivers I am using on my system?"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by novafluxx on 2009-04-13
Everything works, but I'm just curious as to how to find out where I can go/search [already know about lspci] to find out what drivers are currently being used for my hardware! Thanks!

---

### Post by adult swim on 2009-04-13
you might try ```
lspci -k
```
it will show you what kernel drivers and modules are in use for your hardware.
if the -k flag doesnt work for you, try ```
lspci -v
```

---

### Post by novafluxx on 2009-04-13
Thank you!

intelfb appears to be the one I'm using.

Thats listed under VGA compatible controller not display controller...

Whats the difference?

Thanks, lspci -v was easier to read, thanks.

---

