---
title: "2 gig swap, 2 gig ram, but hibernating doesnt work"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by libihero on 2009-01-24
i partitioned my hard drive so that the swap is 2 gigs, like my ram, but when i try to hibernate it just gives me a black screen and the power doesnt shut off

---

### Post by dnRoyston on 2009-01-24
How long did you let it sit there?
Also, did you try suspend to disk?

---

### Post by libihero on 2009-01-24
i let it sit for two minutes for both sleep and hibernate, and for both all i get is a black screen with a flashing white "text prompt thing", but it doesnt let me type.

---

### Post by libihero on 2009-01-25
bumpp
hibernate is really important for me, i have a laptop

---

### Post by taurus on 2009-01-25
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
free -m
```

---

### Post by mjheagle8 on 2009-01-25
you are supposed to have twice the size in swap as your ram.

---

