---
title: "how do I rotate all pages a pdf document by a certain amount with pdftk?"
date: 2009-10-19
forum: New to Ubuntu
---

### Post by pythonscript on 2009-10-19
I have a pdf document that consists of scans from a book, and I'd like to rotate every page in the document by a certain amount, using pdftk. How would I do this? Is is possible to rotate just one page? I couldn't decipher the man pages for it, so I'm wondering if anyone has any experience with this. Thanks!

---

### Post by kaibob on 2009-10-19
> **pythonscript said:**
> I have a pdf document that consists of scans from a book, and I'd like to rotate every page in the document by a certain amount, using pdftk. How would I do this? Is is possible to rotate just one page? I couldn't decipher the man pages for it, so I'm wondering if anyone has any experience with this. Thanks!

I believe pdftk will only rotate pages of a PDF document in 90-degree increments, with the rotation being designated by the first letter of the points of a compass. If in.pdf is a 3-page document, the following rotates page 1 by 90 degrees, page 2 by 180 degrees, and makes no change to page 3:

```
pdftk in.pdf cat 1E 2S 3 output out.pdf
```

If the PDF document contains 10 pages and you want to rotate all pages 90 degrees, the command would be:

```
pdftk in.pdf cat 1-10E output out.pdf
```

---

### Post by KIAaze on 2009-10-19
Try PDF shuffler: [http://sourceforge.net/projects/pdfshuffler/](http://sourceforge.net/projects/pdfshuffler/) :)
It does 0,90,180,270 degrees rotations. Not sure about other angles.
Also allows rearranging, deleting pages and is very easy to use (GUI).

---

### Post by entropy1 on 2009-10-19
[http://www.accesspdf.com/pdftk/](http://www.accesspdf.com/pdftk/)
has several easy-to-follow examples.
I can never remember them, so I keep this webpage bookmarked for easy reference :)

See also
[http://ubuntuforums.org/showthread.php?t=927940&highlight=pdf-shuffle](http://ubuntuforums.org/showthread.php?t=927940&highlight=pdf-shuffle)
for a nice script to rotate only the even pages.

---

