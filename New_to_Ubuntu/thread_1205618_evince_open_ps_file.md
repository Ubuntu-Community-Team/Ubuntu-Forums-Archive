---
title: "evince open ps file"
date: 2009-07-06
forum: New to Ubuntu
---

### Post by flylehe on 2009-07-06
Hi,
I come across this problem with evince opening a ps file
> 
$ evince ./slides.ps 
evince: /build/buildd/cairo-1.8.0/src/cairo-xlib-surface.c:934: _draw_image_surface: Assertion `ret != 0' failed.
Aborted

Thanks for your help!

---

### Post by carml on 2009-07-06
As far as I know eince should be able to read both .pdf and .ps,maybe your .ps is corrupt?

---

### Post by flylehe on 2009-07-06
Yes, I think it is some particular ps files that evince cannot open. Seems that these files has some unusual layout of pages, like landscape style. Here is one example [http://www.kyb.tuebingen.mpg.de/bs/people/weston/svmpractical/svmpractical-slides.zip](http://www.kyb.tuebingen.mpg.de/bs/people/weston/svmpractical/svmpractical-slides.zip). Thanks!

---

### Post by ubu_can on 2009-08-11
Well, on my ubuntu 9.04 installation, a certain .ps file cannot be opened (evince 2.26.1). However, the same .ps file can be opened on my ubuntu 8.10 installation (evince 2.24.1)
Any explanation?

---

