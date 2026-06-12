---
title: "PDF printing: how to..."
date: 2010-10-29
forum: New to Ubuntu
---

### Post by Robert.Thompson on 2010-10-29
Hello:

Is it possible to get OpenOffice, by default, to print to and then open a pdf file which can then be saved?

I have installed, I think, a PDF printer which I can access from OpenOffice but, when I 'print', I have no idea where it goes - it certainly does not open on my desktop.

Any help would be appreciated.

---

### Post by Old_Man_Unix on 2010-10-29
OpenOffice will recognize a PDF file and will attempt to open it - actually, import it - but IME the filters do not work all that well and you often end up with garbage.  

If you can get it to open the file "cleanly", you should be able to print to any *properly installed* printer.  Is the printer installed properly?  Are you able to print other files from OpenOffice?  

BTW, Ubuntu has a  document reader as part of the default installation.  It is called ***Evince***. It reads PDF files very nicely and will print them to any installed printer.   

However, you do not launch Evince from the Main Menu.  You launch it by clicking on the PDF file. Or you can launch it via a terminal command

Is there some reason that you cannot use the document reader for what you want to do?

---

### Post by migs73 on 2010-10-29
Try this
[http://extensions.services.openoffice.org/project/pdfimport](http://extensions.services.openoffice.org/project/pdfimport)

FYI opens as an Impress file to allow editing, and then converts back to PDF on saving. To install, download correct file to desktop, open an OO app and select tools > extension manager.. click add, then browse to your desktop and select the file. Do the legal stuff with the license and accept. Then give it a try!

It's not perfect, layouts can be a bit bodged, depends on what you are trying to do

---

### Post by mike555 on 2010-10-29
Ubuntu has a built-in PDF "printer" , just click print , choice "to file", pick .PDF , name the file (this is important, otherwise it will save as .PDF - which is a hidden file).

---

### Post by ajgreeny on 2010-10-29
I assume you are also aware of the ability OOo has to **export** any document you have written or drawn, etc etc to a pdf instead of the default ODS or ODT.  This option does not show in the print dialog, but in the menu **file ->Export as PDF**.

As far as I'm aware, you can not import a PDF to OOo Draw and then edit it, or at least, I have never been able to do so with any PDFs other than those produced in OOo by exporting as PDF.  Other PDFs such as those downloaded from the web all seem to be non-editable.

There is a package called pdfedit available in the repos which purports to be able to do that, but I have never managed to get it to work very well either.

---

### Post by migs73 on 2010-10-29
> **ajgreeny said:**
> 

As far as I'm aware, you can not import a PDF to OOo Draw and then edit it, or at least, I have never been able to do so with any PDFs other than those produced in OOo by exporting as PDF.  Other PDFs such as those downloaded from the web all seem to be non-editable.



see my post #3 above

---

### Post by ajgreeny on 2010-10-29
> **migs73 said:**
> see my post #3 above
I already have **pdfimport** extension installed, and it will import and open pdf files with no problem, however, as I said, I can not edit most pdf files; only those that I have produced myself with **OOo -> Export to PDF** will edit as far as I can see.

---

### Post by migs73 on 2010-10-29
I've never had any problem editing PDF from any source, only the layout can get a bit jumbled, making it difficult to put text in boxes. I assume any I make will edit without any problems.

---

### Post by uRock on 2010-10-29
This is how I make a PDF.

---

### Post by migs73 on 2010-10-29
Me too :P

---

### Post by ajgreeny on 2010-10-30
> **migs73 said:**
> I've never had any problem editing PDF from any source, only the layout can get a bit jumbled, making it difficult to put text in boxes. I assume any I make will edit without any problems.
OK, I've now investigated my problems a bit further and have found my problem is just that; my problem and not the OOo application extension at all.  I simply had not looked closely enough at the opened pdf in OOo Draw, and had missed a number of the controls.

That's what I like about this forum: you learn a great deal about things sometimes that you don't even know you did not know, to misquote George Bush!

---

### Post by migs73 on 2010-10-31
> **ajgreeny said:**
> OK, I've now investigated my problems a bit further and have found my problem is just that; my problem and not the OOo application extension at all.  I simply had not looked closely enough at the opened pdf in OOo Draw, and had missed a number of the controls.

That's what I like about this forum: you learn a great deal about things sometimes that you don't even know you did not know, to misquote George Bush!

If there is anything else that you don't know , you don't know don't be afraid to ask!

:lol:

---

