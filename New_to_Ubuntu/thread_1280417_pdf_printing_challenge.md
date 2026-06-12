---
title: "pdf printing challenge"
date: 2009-10-02
forum: New to Ubuntu
---

### Post by expatCM on 2009-10-02
I am printing out a large pdf document.  The source pages are about A5 size and since I am printing on A4 I have changed the orientation to Landscape and printing two pages on each sheet.  That works except for one thing.

The printed pages are lining up very close to the top of the page but there is lots of space at the bottom.  This gets in the way of binding since a line of punched holes will take out the first line of type.  I have considered changing the binding from the top to the left but whilst it is a bit better it is still a problem.

There does not appear to be any way to adjust the printed margin.  The printer does not support this and neither does Document Viewer.

Does anyone know of a straight forward solution?

---

### Post by stinger30au on 2009-10-02
what sort of printer are you using??

if it is not fully supported i might suggest you try linux turbo print

[http://www.turboprint.info/](http://www.turboprint.info/)


or you could try and burst the pdf document with pdftk and convert them to jpeg and try again with the jpegs

---

### Post by expatCM on 2009-10-02
The printer is an HP LJ 1200 

I am just downloading turboprint to see what it does ...  Thanks for the suggestion.

Bursting to jpg and working the individual pages is an interesting idea but with 457 pages I am not so sure that I could manage.

---

### Post by expatCM on 2009-10-02
Just been exploring with PDFEdit.  

It seems that you can change the Page Metrics or more likely set a Page Transformation Matrix.  Changing the page metrics gives some strange results and so I will try the page transformation matrix and see what happens.

---

### Post by anaconda on 2009-10-02
What program are you using?

I have often noticed that adobe reader is the best program for printing pdf:s in ubuntu.

It offers more possibilities for adjusting the print settings.

---

### Post by expatCM on 2009-10-02
I have been using Document Viewer 2.26.1 (evince) to try and print.

I have just been playing with PDFEdit.   I am probably working the program the wrong way since I can only manipulate one page at a time.  

I open the file and go to Page / Page Transformation / Page Translate and then change the ty value to -50 and the page drops to where I need it.

However ....  this only applies to one page and I have a lot of them.  I am now looking for a setting to apply the transformation to all page in the document rather than just one.

I will however download Adobe Reader and see if that helps :)

---

### Post by expatCM on 2009-10-02
So as not to lead this thread off track I will open a fresh thread on PDFEdit.

---

