---
title: "Creating PDF's?"
date: 2009-11-26
forum: New to Ubuntu
---

### Post by mvdoso on 2009-11-26
My friend wrote a book (she's 13 and not the *best *writer) and wants to release it under Creative Commons license and she wanted me to create a PDF of it, create a writers website for her, and let people download the PDF.  How do I turn an AbiWord Document into a PDF?  And how do I upload it to Google Sites for download?

---

### Post by cascade9 on 2009-11-26
I'm not sure if you can convert to .pdf with abiword, but its easy with open office. OO-> file-> export as PDF.

---

### Post by kansasnoob on 2009-11-26
I think you can choose to open that with evince.

Let me do some fiddling.

---

### Post by rustutzman on 2009-11-26
Use CUPS pdf printer and just print it to a pdf.

Russ

edit: check Synaptic for cups-pdf. After you install the cups-pdf you open Abiword go to print and select the PDF printer option.

---

### Post by cariboo on 2009-11-26
When you use print to file in the printer dialog it saves the file as a .ps, you can use ps2pdf, it's in the repositories, to convert it to a pdf.

---

### Post by dje on 2009-11-26
try installing the cups-pdf package:
```
sudo apt-get install cups-pdf
```
it creates a 'virtual' pdf printer and it should allow you to create a PDF from any program that supports printing

hope that helps,
dje

---

### Post by PGScooter on 2009-11-26
can you print to PDF?

Go to print, then choose "print to file" and make sure that pdf and not ps is selected.

---

### Post by cariboo on 2009-11-26
I just had a look at the dialog box, you can tell it to save as a pdf.

---

### Post by kansasnoob on 2009-11-26
Yes, many have it right:

[ATTACH]137714[/ATTACH]

---

