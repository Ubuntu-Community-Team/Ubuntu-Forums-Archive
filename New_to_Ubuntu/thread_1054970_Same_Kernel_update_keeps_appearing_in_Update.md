---
title: "Same Kernel update keeps appearing in Update?"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by Roving Sign on 2009-01-30
2.6.27.11 - Pretty sure this is the third time this has appeared in my updates...

I let it update each time and manager says "System up to date"

Next morning - Kernel update is back...

Just me? 

When did this recent kernel appear?

---

### Post by blazemore on 2009-01-30
If you update from the command-line,

```
sudo apt-get upgrade
```

Does it give you an error when installing the kernel package?

---

### Post by Temposs on 2009-01-30
I think they messed up a few things on these kernel updates, so they're releasing fixes. I know the first of the recent kernel updates messed up my graphics driver, but the second of the kernel updates fixed the problem.

---

### Post by Roving Sign on 2009-01-30
This is on both of my Unbuntu machines...btw.

I'll try the command line on the second machine...already ran update on the other...

---

### Post by Roving Sign on 2009-01-30
> **Temposs said:**
> I think they messed up a few things on these kernel updates, so they're releasing fixes. I know the first of the recent kernel updates messed up my graphics driver, but the second of the kernel updates fixed the problem.

Do these fixes get a seperate version number? or just are they just taking a mulligan and repeating the update?

---

### Post by Gulyan on 2009-01-30
This is what I found in my install logs:
```

2009-01-29 16:31:55 status installed linux-image-2.6.27-11-generic 2.6.27-11.26
[...]
2009-01-30 12:56:50 status installed linux-image-2.6.27-11-generic 2.6.27-11.27

```

I agree with Temposs, they're releasing fixes

---

### Post by Roving Sign on 2009-01-30
no errors updating from commandline...

---

### Post by jeffjanzen on 2009-01-30
linux-image-2.6.27-11-generic 2.6.27-11.27-redundant 2.6.27-11.27b!

why isn't it called linux-image-2.6.27-11.27-generic!? then i would've caught that it's actually a newer version of 2.6.27-11....

---

