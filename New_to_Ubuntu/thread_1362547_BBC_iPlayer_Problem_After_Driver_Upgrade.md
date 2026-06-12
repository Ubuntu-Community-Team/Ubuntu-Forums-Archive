---
title: "BBC iPlayer Problem After Driver Upgrade?"
date: 2009-12-23
forum: New to Ubuntu
---

### Post by mapes12 on 2009-12-23
I've just loaded the new Nvidia driver version 195 (from 190) as recommended in Hardware Drivers but now I can't play anything on the BBC iPlayer site.

With 190 I could play in normal screen (albeit with choppy video) but now when I click on a programme to play the video doesn't come up. I get a black screen in the middle where the video normally is.

Any ideas :confused:

---

### Post by philinux on 2009-12-23
> **mapes12 said:**
> I've just loaded the new Nvidia driver version 195 (from 190) as recommended in Hardware Drivers but now I can't play anything on the BBC iPlayer site.

With 190 I could play in normal screen (albeit with choppy video) but now when I click on a programme to play the video doesn't come up. I get a black screen in the middle where the video normally is.

Any ideas :confused:

You must have a ppa active and I bet thats a beta driver. Beta= breakage may occur. :P

[http://www.phoronix.com/scan.php?page=news_item&px=NzgzNw](http://www.phoronix.com/scan.php?page=news_item&px=NzgzNw)

---

### Post by MattM11 on 2009-12-23
I had (what sounds like) the same problem this morning (although I haven't updated any drivers recently). I had to boot into Vista to get iPlayer to work properly. However, I've just checked it (in Ubuntu 9.10) and it seems to be working fine again.

---

### Post by laidback on 2009-12-23
Check that you haven't got:-

swfdec-mozilla
or
Gnashxxx

loaded. (use synaptic)
If you have delete them.

---

### Post by mapes12 on 2009-12-23
> You must have a ppa active and I bet thats a beta driver. Beta= breakage may occur. Spot on! I'd forgotten I'd added the repo. Many thanks. All now sorted :guitar:

---

