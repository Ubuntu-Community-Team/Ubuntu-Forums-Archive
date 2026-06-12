---
title: "Ugly Website Fonts (Helvetica?)"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by seuzy13 on 2009-01-10
I have been having a problem with a particular font on the web. Occasionally, I'll come across a website with fonts that look just awful. I have checked a couple times and each time it was the Helvetica font causing the problem. I'm not sure if I have this font installed or not. Maybe this will help:

$ locate Helvetica
/opt/openoffice.org/basis3.0/share/psprint/fontmetric/Helvetica-Bold.afm
/opt/openoffice.org/basis3.0/share/psprint/fontmetric/Helvetica-BoldOblique.afm
/opt/openoffice.org/basis3.0/share/psprint/fontmetric/Helvetica-Oblique.afm
/opt/openoffice.org/basis3.0/share/psprint/fontmetric/Helvetica.afm
/usr/share/matplotlib/mpl-data/fonts/pdfcorefonts/Helvetica-Bold.afm
/usr/share/matplotlib/mpl-data/fonts/pdfcorefonts/Helvetica-BoldOblique.afm
/usr/share/matplotlib/mpl-data/fonts/pdfcorefonts/Helvetica-Oblique.afm
/usr/share/matplotlib/mpl-data/fonts/pdfcorefonts/Helvetica.afm

Is there something I need to fix here in order to get the font looking better? I thought if I didn't have the font installed, it would skip that one and go to the next on the list, but it doesn't seem to be doing that either.

---

### Post by jrusso2 on 2009-01-10
You have to pay for Helvetica since I think Adobe has the license although there are clones.

---

### Post by seuzy13 on 2009-01-10
So what are those .afm files I have on my system?

And, if that's the case, the website should fall back on the font they list after Helvetica in the CSS style sheet right? (Arial or sans serif, e.g.)

---

### Post by albinootje on 2009-01-10
> **seuzy13 said:**
> So what are those .afm files I have on my system?

And, if that's the case, the website should fall back on the font they list after Helvetica in the CSS style sheet right? (Arial or sans serif, e.g.)

You have msttcorefonts or/and ttf-liberation installed ?
```

sudo apt-get install ttf-liberation msttcorefonts

```

See also :
[https://www.redhat.com/promo/fonts/](https://www.redhat.com/promo/fonts/)
[http://en.wikipedia.org/wiki/Liberation_fonts](http://en.wikipedia.org/wiki/Liberation_fonts)
[http://brainstorm.ubuntu.com/idea/11444/](http://brainstorm.ubuntu.com/idea/11444/)

---

### Post by seuzy13 on 2009-01-10
Yeah. Both installed.

---

