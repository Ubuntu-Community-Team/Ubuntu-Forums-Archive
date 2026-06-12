---
title: "removing HAL"
date: 2010-03-25
forum: New to Ubuntu
---

### Post by Fika on 2010-03-25
Is there any way to remove HAL and still have networking capabilities in ubuntu 9.04?

---

### Post by HermanAB on 2010-03-25
Not easily no.  However, the next release of Ubuntu will probably be free of HAL, since it is being replaced in all distros.

---

### Post by Tom.Gee on 2010-03-25
It's already 2010.  According to the IMDB, HAL was removed in 2001: [http://www.imdb.com/title/tt0062622/synopsis](http://www.imdb.com/title/tt0062622/synopsis)

---

### Post by Mykk on 2010-03-25
I thought if you removed HAL nothing hardware wise will work?

Somebody clear this up for me? :)

---

### Post by Nepherte on 2010-03-25
> **Mykk said:**
> I thought if you removed HAL nothing hardware wise will work?
That is incorrect. 

Currently, The X windowing system (the graphical layer) relies on hal. Since hal is now deprecated, the new X server (1.8) will not depend on hal anymore but on udev directly. So if you'd like to remove hal, you'll end up without a gui in ubuntu.

The network aspect does not depend on hal, so reomving hal will not affect it.

---

