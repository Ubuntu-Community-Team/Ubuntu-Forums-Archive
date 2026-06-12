---
title: "exporting to pdf without opening the file"
date: 2009-07-13
forum: New to Ubuntu
---

### Post by jtsc on 2009-07-13
Hello, I have an extremely large .doc file... either because it is hundreds of pages long or because of it being almost completely formatted in tables, Open Office, AbiWord, and KWord all freeze when they try to open it. (I know there is nothing wrong with the file itself... I've sucessfully opened it with several different versions of MWord.) I would like to turn the file into a pdf, but the only way I know to do *that* is from inside one of the word processors... is there a command or utility that will let me make a pdf without opening the document first?

Thanks! I'm using 9.04.

---

### Post by Xero Xenith on 2009-07-13
Perhaps you could bully a web site into doing it for you? :lolflag:

[http://www.doc2pdf.net/](http://www.doc2pdf.net/)

---

### Post by jtsc on 2009-07-13
Blush. Thanks XX. I'm still interested in knowing how I would go about converting a document without opening it and without internet access, though!

---

### Post by AlexCunha on 2009-07-13
Some tips here: [http://ubuntuforums.org/showthread.php?t=674878](http://ubuntuforums.org/showthread.php?t=674878)

---

### Post by niteshifter on 2009-07-13
> **jtsc said:**
> Blush. Thanks XX. I'm still interested in knowing how I would go about converting a document without opening it and without internet access, though!

Let's see if the simple way works first. In Terminal type:
```
ooffice -pt PDF_file_generator *yourdocument.doc*
```

Notes:
Change *yourdocument.doc* to whatever path/filename you need.
You'll need cups-pdf installed. Check your printers list for a printer named PDF_file_generator. Not present? Then install cups-pdf:
```
sudo apt-get install cups-pdf
```
If you had to install cups-pdf, you need to make the PDF folder in your home folder:
```
mkdir PDF
```
Must be named exactly that - PDF - not Pdf or pdf. Must be in the user's home folder that invokes the print job.
The metadata of the pdf produced (Title, Auther, Subject, etc) may not be to your liking. Use pdftk to fix up:
```
sudo apt-get install pdftk
man pdftk  

```

Rumor has it that OOo is compatible with MSOffice docs. By and large it is so long as the MSOffice document is "well behaved". MSO docs of very complex structure or whose roots go back to Office '97 and have had odd reformating done to them so they work in later versions of MSO (vs redone, like they should have been), they can fail to convert properly.

I can almost promise you it's not the size, I've produced documents hundreds of pages long - complex docs via OOo Writer with Calc, Math and Draw embeds  - but they were pure Open Document Format docs.

So if the above simple trick doesn't pan out for you: It is possible to produce pdf output within Windows sans Adobe software, free software to boot: Via Ghostscript and GSView. See these links:
[http://pages.cs.wisc.edu/~ghost/gsview/](http://pages.cs.wisc.edu/~ghost/gsview/)
[http://www.stat.tamu.edu/~henrik/GSWriter/GSWriter.html](http://www.stat.tamu.edu/~henrik/GSWriter/GSWriter.html)
I've used Ghostscript and GSView on Windows for years. It's a bit tedious to setup, but it works. I then use pdftk on Linux to edit the metadata.

---

