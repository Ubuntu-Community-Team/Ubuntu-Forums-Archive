---
title: "Problems compiling latex in Kile"
date: 2009-09-27
forum: New to Ubuntu
---

### Post by jandalchick on 2009-09-27
I'm having some problems with Kile.  Latex code I'd previously written (and successfully compiled) in winedit won't work from Kile, it seems that some of the packages I used aren't available in Kile but the main issue is all my images are post-script (this was the easiest way to make things work with winedit) and from what i can gather from reading online help files is that I need to change these to pdfs.  This seems a bit of a pain - is there no way to use my post-script files directly as I have been up till now?

I've tried adding a couple of chapters to my document in the same way as I have before:
ie \include{Discussion} and a file Discussion.tex.  This doesn't work, and I get the error No file Discussion.aux.   I'm sure in windedit the aux files were generated automatically, do I need to do something different in Kile to get these aux files?

Also there seem to be no help files, I just get: There is no documentation available for /kile/index.html.

Argh!  I'm pretty inexperenced with both linux and latex, just try to learn enough to do what i need to do so if anyone can help it would be much appreciated.

cheers!

---

### Post by XCan on 2009-09-28
Have you tried compiling it from a terminal? If not posting the error message from such a compilation should help to lock down the error, simply run 
```
 cd /path/to/the/dir/of/your/tex
latex yourtexdoc.tex

```

Also, there is no reason why .eps would not work and .pdf would. I run through plenty of .eps images in my documents. I would guess that your issue is a missing package which the above command will tell us. :)

---

### Post by Stefan_K on 2009-09-28
Hi,

if you are using postscript files click on *LaTeX* instead of *PDFLaTeX*. Or use the [epstopdf package]("http://ctan.org/pkg/epstopdf-pkg") or the [epstopdf program]("http://ctan.org/pkg/epstopdf") and use PDFLaTeX.

Stefan


--
[TeXblog]("http://texblog.net")

---

