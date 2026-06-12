---
title: "Radeon no longer seems &quot;accelerated&quot; in Jaunty upgrade"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by lumix on 2009-05-03
I did the online upgrade from Intrepid, and now video is very slow, and nothing shows up (at all) in Hardware Drivers.

Any ideas?

---

### Post by nandemonai on 2009-05-03
> **lumix said:**
> I did the online upgrade from Intrepid, and now video is very slow, and nothing shows up (at all) in Hardware Drivers.

Any ideas?

What card? ATI dropped support for a lot of older cards in their restricted driver.

---

### Post by lumix on 2009-05-04
It's a built-in for a Compaq laptop. I can't remember the model off the top of my head, but it was supported in Intrepid, and showed up in restricted drivers there.

---

### Post by Didius Falco on 2009-05-04
Open a Terminal shell and type ```
lspci | grep VGA
``` and post the output here. That will tell you what kind of video card you have.

---

