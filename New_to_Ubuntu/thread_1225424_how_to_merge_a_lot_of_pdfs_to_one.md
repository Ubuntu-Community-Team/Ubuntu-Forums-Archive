---
title: "how to merge a lot of pdfs to one?"
date: 2009-07-28
forum: New to Ubuntu
---

### Post by heyyy on 2009-07-28
i have this problem :
i want to print on file-s(1,2,3,...) the search results from a web page and then merge those files into one
any ideas?

---

### Post by heyyy on 2009-07-28
maybe a program to edit pdfs?

---

### Post by XCan on 2009-07-28
pdftk will do it beautifully, it's in synaptics. Use

```
 pdftk file1.pdf file2.pdf file3.pdf file4.pdf cat output merged.pdf
```

---

### Post by heyyy on 2009-07-28
> **XCan said:**
> pdftk will do it beautifully, it's in synaptics. Use

```
 pdftk file1.pdf file2.pdf file3.pdf file4.pdf cat output merged.pdf
```

thanks but i'll need to do some text editing as well

---

### Post by XCan on 2009-07-28
You can edit either the individual files or the merged file using pdfedit.

---

### Post by llamabr on 2009-07-28
By text editing, you mean you want to edit the text inside the pdf pages, and them merge them into one?

It depends on how the pdfs were made.  if you made them with, e.g., LaTeX, it would be easier to edit the source and recompile.  If they're old scans of images like journal articles, it won't work.  If they're recent, Openoffice 3.0 now comes with a pdf editor:

[http://extensions.services.openoffice.org/project/pdfimport](http://extensions.services.openoffice.org/project/pdfimport)

---

### Post by heyyy on 2009-07-28
> **llamabr said:**
> By text editing, you mean you want to edit the text inside the pdf pages, and them merge them into one?

It depends on how the pdfs were made.  if you made them with, e.g., LaTeX, it would be easier to edit the source and recompile.  If they're old scans of images like journal articles, it won't work.  If they're recent, Openoffice 3.0 now comes with a pdf editor:

[http://extensions.services.openoffice.org/project/pdfimport](http://extensions.services.openoffice.org/project/pdfimport)

i thimk this features comes preinstalled with open office.. i tried to open it with it but i cant figure out the encoding...some help?
the pdfs were created by printing to a file by firefox 3.5 to pdf format

---

### Post by heyyy on 2009-07-28
is there a way to  check what character encoding a pdf has?

---

### Post by llamabr on 2009-07-29
I don't think it comes pre-loaded with ooffice.  I believe you need to add the extension.  And note that you must be running version 3.0

---

### Post by spcwingo on 2009-07-29
I believe pdfedit will do exactly what you want (edit pdf text, merge pdfs, etc).  It's in the repos.

---

### Post by llamabr on 2009-07-29
pdfedit is great, assuming that the pdfs are edit-able.

---

### Post by PGScooter on 2009-07-29
pdfedit is an option. I would personally go for pdftk to merge them and OOo to edit them. See here for installing the OOo plugin: [http://ubuntuforums.org/showthread.php?t=829479](http://ubuntuforums.org/showthread.php?t=829479)

---

### Post by tazztone on 2009-11-27
to merge you can also use pdfsam [http://www.pdfsam.org]("http://www.pdfsam.org/")

---

### Post by kendoori on 2009-11-27
If you are a GUI person, PDF Shuffler works great for merging, adding pages, deleting pages. It will not do inline edits [http://sourceforge.net/projects/pdfshuffler/](http://sourceforge.net/projects/pdfshuffler/)

---

