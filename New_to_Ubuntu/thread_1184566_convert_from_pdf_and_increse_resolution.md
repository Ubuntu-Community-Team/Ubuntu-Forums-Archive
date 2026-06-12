---
title: "convert from pdf and increse resolution?"
date: 2009-06-11
forum: New to Ubuntu
---

### Post by stinger30au on 2009-06-11
i have a number of pdf files at are over 100 pages in length

i know i can burst them to jgp with convert if i do this


convert myfile.pdf myfile.jpg

this works well, *BUT* id like the jpg files to be of higher resolution say 200 dpi at least. the original pdf looks like magic, but the jpg files are *VERY* low resolution

i have done a

man convert

and i cant see a dpi setting for output, maybe i missed it

can someone help me out??

thanks

---

### Post by Mornedhel on 2009-06-11
convert has a -quality [value] option you can use for JPEG/MIFF/PNG compression level (from the man page, apparently you missed it). You can try this. You could also try using PNG instead of JPEG ; this usually works better with jagged edges (for instance, scanned text) than JPEG, since it doesn't result in compression artifacts like JPEG does.

---

### Post by kaibob on 2009-06-11
> **stinger30au said:**
> <snip>i have done a man convert and i cant see a dpi setting for output, maybe i missed it can someone help me out?? Thanks

The following page shows all available options for convert. Click on an option to obtain more detail. There are a number of options that affect quality, and I don't know which one will improve the quality of the output JPG.

[http://www.imagemagick.org/script/convert.php](http://www.imagemagick.org/script/convert.php)

---

### Post by hessiess on 2009-06-11
Dont use jpg for images containing sharp transitions.

---

### Post by mcduck on 2009-06-11
"-density" is the option used to set the image DPI attribute, and in this case you'll have to use the density option before reading the PDF file as you wish to set the DPI at which the images are extracted from the PDF, not the density attribute of the resulting image (which wouldn't have any real effect on image quality). In ther words, you want to set the DPI of *input*, not *output*.

"-quality" is then used to set the image compression quality for the final image, for JPG it's a range between 0 and 100, 100 being the best quality and lowest compression.

Try this:
```
convert -density 300 myfile.pdf -quality 90 myfile.jpg
```

Play around with the "density" setting, the images in your PDF have certain size and going above that will not improve image quality, quite the opposite. Of course you can change the "quality" as well, but 90 is probably even a bit too much and if you want higher quality compression than that you should be using some other image format than JPG anyway. ;)

Edit: Just to explain the difference between image quality in your PDF files, and the quality of output images.. Imagemagick assumes default density of 72, which is great for any display graphics. But your PDF was probably made for print, uisng higher DPI (300 would be pretty much standard). So, simple convert will read the 300DPI image at 72DPI density and then output that to JPG. Result should look the same size (as in inches, or centimeters) on your screen as the original does, but will of course have much less pixels.

---

### Post by stinger30au on 2009-06-11
awesome, thanks for the feedback everyone

---

