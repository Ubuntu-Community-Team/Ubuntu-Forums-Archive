---
title: "combining PDFs in one"
date: 2010-03-11
forum: New to Ubuntu
---

### Post by DarinB on 2010-03-11
Is there a simple way to combine many pdfs in one? Not two or three but about a 200. I saw something about doing it in breezy but it was command line and very labor intensive. 
would be nice if i could just drag them all into a pdf container of some kind. ????

---

### Post by lotharmat on 2010-03-11
Try [Here]("http://ubuntuforums.org/showthread.php?t=411396") - I guess this would be too labour intensive though.

---

### Post by DarinB on 2010-03-11
I tried pdf edit but not too easy to use i found this application for deb.
pdfsam_1.1.3-2_all not sure if it will kill something else it seemed to add a ton of java libs that always scares me...it worked really easily. 
i hope it won't cause any problems. if i need to remove it will it take out all the java stuff it added as well???? but that is not a question for here maybe. it sounds like a more basic ubuntu question. on adding and removing packages and whether to remove or completely remove, to which i am not sure that means either. but the above was a breeze to use. real ugly gui though but who cares for what i need.

---

### Post by sybille on 2010-03-11
PDF-Shuffler is another alternative. It's simple and easy: drag and drop PDF files from your file manager, rearrange or delete pages as needed, then export as a new PDF.

PDF-Shuffler is available in Ubuntu (universe repository). More info and screenshots here:
[http://sourceforge.net/projects/pdfshuffler/](http://sourceforge.net/projects/pdfshuffler/)

---

### Post by marbertone on 2010-03-11
I heard about that... I report from the original site:

```

 gs -q -sPAPERSIZE=a4 -dNOPAUSE -dBATCH -sDEVICE=pdfwrite -sOutputFile=out.pdf in1.pdf in2.pdf in3.pdf 

```

Cheers!
Mario Alberto

---

### Post by DarinB on 2010-03-11
that is good if you have to add only a few pages but to command line hundreds even tens of pages would make that impractical
but thanks anyway 

i will try pdf shuffler

---

### Post by DarinB on 2010-03-11
PDF shuffler ROCKS! easy in the repos. 
it may not do much more than merge and shuffle but it is exactly what was needed 
THANKS!!!!!!

---

### Post by kaibob on 2010-03-11
> **DarinB said:**
> that is good if you have to add only a few pages but to command line hundreds even tens of pages would make that impractical
but thanks anyway 

i will try pdf shuffler
The pdftk utility is a good command-line solution because you can use globbing. All you have to do is copy the source pdf files to an empty directory, open a terminal window and change to that directory, and enter:

```
pdftk *.pdf cat output new.pdf
```

There are two issues with this solution. First, although pdftk is a small utility, it has a large number of dependencies, so be sure to check size before installing. Also, you cannot specify the order in which the source pdf's are added to the master pdf except by renaming them.

EDIT: Just saw your post about PDF shuffler. Glad you found a good solution.

---

### Post by Fenris_rising on 2010-03-11
Fantastic! I had just compiled 150 A4 jpg images into a single PDF when a correction was posted on the source website =/ I was wondering how I was going to break the PDF document back up to change the one page as I had deleted the seperate images on completion.

This site, and Ubuntu, simply rock!

regards

Fenris (spiffingly impressed yet again!!)

---

### Post by vratnica on 2010-05-20
pdftk rocks!

Thank you, dude, great solution!=D>

---

