---
title: "Program to compress pdf?"
date: 2010-08-13
forum: New to Ubuntu
---

### Post by Miguellint on 2010-08-13
Hi all....

I used imagemagick to combine eight jpgs into a pdf. 

```
convert *.jpg   outputfile.pdf
```

The combined size of the original jpg's was about 4MB. The resulting pdf was 14MB

I tried gscan2pdf to compress the pdf file (as suggested in another thread) but it made little difference.

Anyone know of another way to compress a pdf. *Not* for storage purposes or else I'd just use zip or rar.

Thanks
Miguel

---

### Post by mapes12 on 2010-08-13
[http://www.pdflabs.com/tools/pdftk-the-pdf-toolkit/](http://www.pdflabs.com/tools/pdftk-the-pdf-toolkit/)

but images are hard to compress lower than what the pdf conversion has already done.

---

### Post by Miguellint on 2010-08-13
I've kept playing around and come up with a solution that works for me by using Scribus. Very repetitive and only suitable if you've no more than a dozen or so jpgs (or plenty of time on your hands). But it turns 4MB of jpgs into a 4MB PDF with no obvious image quality loss so that's good enough for me.

If you're moderately comfortable using Scribus then just start a new page, insert a new jpg and repeat ad nauseum. Then File/Export/SaveAsPDF

In a bit more detail....

Page/Insert/Insert1Page/OK

Insert/ImageFrame, then drag to cover entire page

Ctrl+D (Get Image) or right-click Get Image

Windows/Properties/Image or F2/Image

Scale to Frame Size +/- Proportional

or if that looks silly just note the X-pos and Y-pos of the image and go to...

Page/ManagePageProperties/Size/Custom

...and adjust the page width and heigth.

Repeat for each jpg

When finished go File/Export/SaveAsPDF

Untick Clip to Page Margins

If you want, play around with Compress Text and Vector Graphics but I just left it on Automatic

It's very long-winded but gets the job done

Miguel

---

