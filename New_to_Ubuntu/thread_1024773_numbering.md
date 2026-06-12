---
title: "numbering"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by szaqlon on 2008-12-29
I am trying to convert .ppm files to .jpg's. I am using convert and can do a lot at one time but I need to number them 0001, 0002, etc. How do I go about doing this, because they number 1, 2, 3, etc and that doesn't work for me.

---

### Post by kaibob on 2008-12-29
You can use %04d to force 4 numbers as in the following:

```
convert *.png %04d.jpg
```

---

### Post by szaqlon on 2008-12-29
Yes, that's exactly what I needed. Thank you.

---

### Post by Dedoimedo on 2008-12-29
> **kaibob said:**
> You can use %04d to force 4 numbers as in the following:

```
convert *.png %04d.jpg
```

Very elegant! I was thinking loop with sed, but yours is much more effective. Nice one.
Dedoimedo

---

