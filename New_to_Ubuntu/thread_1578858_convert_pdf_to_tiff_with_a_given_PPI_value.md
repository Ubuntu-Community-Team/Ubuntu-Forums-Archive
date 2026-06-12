---
title: "convert pdf to tiff with a given PPI value"
date: 2010-09-21
forum: New to Ubuntu
---

### Post by sundol on 2010-09-21
What is the option of "convert" command to convert a.pdf to a.tiff with a given DPI(pixels per inches) value (e.g. 600)?
Currently, I use GIMP to do same thing but "convert" would be simpler.
I tried "convert" with an option of --resample but it didn't work. Any one can give an example?

Thanks in advance

---

### Post by niteshifter on 2010-09-21
Hi,

```
convert a.pdf -density {dpi_value} -resample {HxV} a.tiff
```
may do what you want.

FYI: the man page on convert is very terse. For a more complete description of ImageMagick's tools point your browser to:
[this local url]("file:///usr/share/doc/imagemagick/www/index.html") (file:///usr/share/doc/imagemagick/www/index.html).

---

