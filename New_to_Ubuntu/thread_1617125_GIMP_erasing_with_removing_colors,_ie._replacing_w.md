---
title: "GIMP: erasing with removing colors, ie. replacing white by transparent"
date: 2010-11-09
forum: New to Ubuntu
---

### Post by frenchn00b on 2010-11-09
Hi guys, using GIMP, I would like to do some erasing with removing colors, ie. replacing white by transparent. However in a JPG it seems not possible :( with pressing "suppr" key after a selection. :( 
Can it be possible?

---

### Post by disk0tek on 2010-11-09
Here you go: [http://aplawrence.com/Linux/crousegif.html](http://aplawrence.com/Linux/crousegif.html)

I actually needed to know how to do that a while ago and it took me forever to find the information.  It was surprisingly easy this time.

---

### Post by mcduck on 2010-11-09
Sure it's possible, just go to Layer/Transparency/Add Alpha Channel, and you'll get your transparency. :)

(of course you'll have to save the image in some other format afterwards, as jpg doesn't support transparency)

---

### Post by disk0tek on 2010-11-09
> **mcduck said:**
> Sure it's possible, just go to Layer/Transparency/Add Alpha Channel, and you'll get your transparency. :)

(of course you'll have to save the image in some other format afterwards, as jpg doesn't support transparency)

Not trying to hijack this thread, and I'm hoping this will be helpful to the OP as well, but do you know what formats other than png support transparency?  Png is the only one I ever use.

---

### Post by mcduck on 2010-11-09
PNG is usually the best one, since it supports full Alpha channel (meaning that you can get partial transparency) and uses lossless compression so any graphics & text stays clear and you don't loose quality if you need to edit your images afterwards.

TIFF does support transparency as well, but is a bit of a mess when it comes to compatibility (it's a common joke to say that TIFF comes from "Thousands of Incompatible File Formats..:D)

GIF does transparency too, but not full alpha channel. That works for some stuff, but without full alpha channel you'll easily run into aliasing issues which is why I wouldn't recommend GIF.

Then there are bunch of other formats, which are all either application-specific or very rarely used and not commonly supported.

In the end, PNG is pretty much the only real option here. Decent compression, excellent quality, and it's well supported.

---

### Post by frenchn00b on 2010-11-10
> **mcduck said:**
> Sure it's possible, just go to Layer/Transparency/Add Alpha Channel, and you'll get your transparency. :)

(of course you'll have to save the image in some other format afterwards, as jpg doesn't support transparency)
tahanks a lot it worked so well

---

