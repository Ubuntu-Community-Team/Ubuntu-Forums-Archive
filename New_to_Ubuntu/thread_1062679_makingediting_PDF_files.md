---
title: "making/editing PDF files"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by ianb72 on 2009-02-07
I wonder if anyone can help me???

I have 6 PDF files, which instead of being put in one document as 6 pages, they have been made into 6 individual files, now I would like to make them into one document with 6 pages, I hope you get what I mean??

Can this be done and what software can I use??

I am using Gusty if that helps

Ian

---

### Post by bennachie on 2009-02-07
A quick-and-dirty approach would be to open the six documents in OpenOffice 3 (open the first one, then add the others in successive pages of the same document). You could then export the whole document as a PDF. 

The following reference describes a more sophisticated approach:

[http://www.wikihow.com/Edit-PDF-Files-in-Linux-Using-GIMP](http://www.wikihow.com/Edit-PDF-Files-in-Linux-Using-GIMP)

While Acrobat Reader is available for Linux, and there are various online PDF services available, there doesn't yet appear to be a fully functional open source replacement for Acrobat. 

I'd be glad to stand corrected on that last statement!

---

### Post by carml on 2009-02-07
You can try to use also an application called PDF editor.

---

### Post by kaibob on 2009-02-07
> **ianb72 said:**
> I have 6 PDF files, which instead of being put in one document as 6 pages, they have been made into 6 individual files, now I would like to make them into one document with 6 pages, I hope you get what I mean??

There are a lot of ways to join individual PDF documents. Two command-line solutions that utiltize Ghostscript and pdftk (both are in the repo's) are:

```
gs -sDEVICE=pdfwrite -dNOPAUSE -dQUIET -dBATCH -sOutputFile=output.pdf inputfiles.pdf
```

or

```
pdftk inputfiles.pdf cat output outputfile.pdf
```

In the above commands, you need to insert the names of the input and output files. When combining a large number of PDF files, it's easiest to place them in an empty directory and use *.pdf as the input files. I generally find pdftk easier to use than Ghostscript.

---

