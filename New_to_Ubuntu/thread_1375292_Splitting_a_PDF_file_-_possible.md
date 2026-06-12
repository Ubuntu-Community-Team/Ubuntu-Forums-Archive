---
title: "Splitting a PDF file - possible?"
date: 2010-01-07
forum: New to Ubuntu
---

### Post by Wheeeze on 2010-01-07
I have a large (9 Mb) PDF document file and wish to split it into small sections for separate users at different times.  Each separate user does not need the whole document, nor would they thank me for sending or linking them such a large file!  Is it possible to split this file into groups of (say) 10 pages at a time?  These smaller files either need to be PDFs or any Open Office extensions because experimentation with copy and paste lost diagrams and KPDF gave me a series of images which we don't want to use.  

If it is possible, what program could I use and what technique should I use?  Many thanks in advance. Regards, Wheeeze

---

### Post by Methuselah on 2010-01-07
Launch Application->Software Center (Add Remove if not Ubuntu 9.10) and enter **pdf split** in the search bar.
There will be a few apps you can try like pdfsam and pdf shuffler.
I haven't used them so I can't recommend any in particular.

---

### Post by rafita on 2010-01-07
pdftk works well

---

### Post by kaibob on 2010-01-07
There are many ways to do what you want--both GUI and command-line. I use Ghostscript with the following command line, which is easily made into a shell script or nautilus script. You need to change the first and last page, and the input and output file. 

```
gs -sDEVICE=pdfwrite -dNOPAUSE -dQUIET -dBATCH -dFirstPage=1 -dLastPage=10 -sOutputFile=output.pdf "input.pdf"
```

BTW, I suspect PDFtk is probably easier to use and should be your first option if you are looking for a command line solution.

---

### Post by Wheeeze on 2010-01-08
Thank you all for your help, now I'm just off to read up on what you've pointed me to!
Regards, Wheeeze

---

