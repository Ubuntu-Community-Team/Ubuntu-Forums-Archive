---
title: "Add bookmarks or ToC to pdf?"
date: 2010-04-27
forum: New to Ubuntu
---

### Post by slughappy1 on 2010-04-27
I was wondering, how I can go about adding a Table of Contents of Bookmarks to a PDF document itself?

---

### Post by Kushal Sejwal on 2010-04-28
When creating a pdf file from scratch via OpenOffice.org Writer, bookmarks are not a problem as they are automatically added into the pdf file according to the formatting done in writer.

But I myself want to know if there exists some way to edit and add bookmarks to any pdf file?

---

### Post by slughappy1 on 2010-04-30
I have around 200 pdfs that I want to combine into OpenOffice Draw. I installed the PDF import extention, but I don't know how to import all the PDFs. When I try and insert file, it tells me "file could not be loaded". I want to combine all the PDFs into one PDF with a ToC. I want to be able to edit the ToC how I see fit, and was told OOo was the only way to go about it.

---

### Post by slughappy1 on 2010-04-30
Do you know how to import lots of PDFs into one document so I could make the ToC? I keep getting an error in Draw when I import file. It says that the file could not be loaded.

---

### Post by meho_r on 2010-04-30
The only way? I wouldn't even think of doing that in OOo. Whether use some of pdf editors (like Adobe Acrobat and similar) or use LaTeX (with package [pdfpages](http://www.ctan.org/tex-archive/help/Catalogue/entries/pdfpages.html)).

---

### Post by kwacka on 2010-04-30
I'd go for pdftk (pdftoolkit).```
pdftk 1.pdf 2.pdf 3.pdf cat output 123.pdf
```

AFAIK, the OO pdf importer means that you'd have to open them one by one and cut/paste each one.

You may be able to list the PDFs to a text file & use that to paste a LONG pdftk command.

---

### Post by ugm6hr on 2010-05-01
I second pdftk - I think there may be a GUI for it too - but haven't tried it yet - I saw it in the Lucid Software Center.

Then just create a ToC on OO Writer and export to PDF, and use pdftk to add that to the front of the new large PDF file.

---

### Post by meho_r on 2010-05-01
And what about bookmarks (i.e. links) using pdftk?

---

### Post by Michael Steinberg on 2010-05-18
I found that Foxit Reader for Windows does bookmarks really well and intuitively; it's free and runs fine in WINE. Alas, Foxit Reader for Linux doesn't.

---

### Post by kaibob on 2010-05-18
> **meho_r said:**
> And what about bookmarks (i.e. links) using pdftk?

I don't believe pdftk will allow you to add or edit bookmarks. You may want to look at the jpdfbookmarks program. I have never used it, but the documents indicate that it can add bookmarks, and it does have an extensive GUI. 

[http://flavianopetrocchi.blogspot.com/](http://flavianopetrocchi.blogspot.com/)

[http://jpdfbookmarks.altervista.org/toc.html](http://jpdfbookmarks.altervista.org/toc.html)

---

### Post by geoffm on 2011-05-26
You can easily add bookmarks and save them using [PDF XChange viewer]("http://www.tracker-software.com/product/pdf-xchange-viewer"), which works well on WINE.
I would really like a program that can create bookmarks from a TOC, though, because most PDFs out there are cruelly lacking bookmarks but a lot have a TOC

---

