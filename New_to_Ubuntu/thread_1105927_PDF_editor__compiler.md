---
title: "PDF editor / compiler?"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by aquascrotum on 2009-03-25
Has anyone come across a better PDF editor than the "PDF Editor" app?

I need an equivalent of Adobe Acrobat - I don't need to edit the pdf per say, just add/remove/compile pages that can vary in page size. PDF editor seems pretty rubbish at that unfortunately.

Any advice appreciated...

---

### Post by Temposs on 2009-03-25
So do you have only a pdf and not the original source documents that make up the pdf pages?

---

### Post by freak42 on 2009-03-25
never used it, but saw it suggested in other threads.

there actually is a pdf importer for open office, maybe that helps:

[http://extensions.services.openoffice.org/project/pdfimport](http://extensions.services.openoffice.org/project/pdfimport)

don't know wheter it is in the repositories or not.

hth

---

### Post by aeiah on 2009-03-25
you can also edit pdfs with inkscape. if you just want to strip out pages, add new pages etc then use something like pdftk. i suspect there may be a gui wrapper for it somewhere too

---

### Post by aquascrotum on 2009-03-25
> **freak42 said:**
> never used it, but saw it suggested in other threads.

there actually is a pdf importer for open office, maybe that helps:

[http://extensions.services.openoffice.org/project/pdfimport](http://extensions.services.openoffice.org/project/pdfimport)

don't know wheter it is in the repositories or not.

hth

Not all pdf's are created from openoffice.....I have GIS drawings, Cad drawings, graphical figures etc, all to be inserted in a report.

>  you can also edit pdfs with inkscape. if you just want to strip out pages, add new pages etc then use something like pdftk. i suspect there may be a gui wrapper for it somewhere too 

Did a quick search and can't find a GUI for it except one partially in German. TBH if you have a 100page document and you need to insert pages here and there, a commandline interface just isn't adequate.

I got sorted using an online compiler at pdfescape.com; not ideal though, and this does seem to be one area where theres a dearth of adequate Linux compatible apps about. I need an Acrobat equivalent that can (easily and in a gui) allow compilation, sort pages, rotate pages, resize pages, auto-number pages, add annotations, etc etc. Its a fairly big deal for anyone thinking seriously of running an office environment on Linux I'd have thought? Might try getting Openoffice 3 later and see what the pdf importer in it can do.

---

### Post by kaibob on 2009-03-25
> **aquascrotum said:**
> Any advice appreciated...
Your question is a common one in this forum, and I have never seen anything that really meets your needs. There is a commercial product that will do what you want, and another Java-based one. Just do a search of the entire forum on the word pdfedit, and you'll find many threads on this issue.

I use PDF documents a lot and have finally settled on the command-line tool pdftk. This is far from an ideal solution, but I have yet to find anything better.

Anyways, do a search on pdfedit and see what other forum members have suggested.

EDIT:

GUI for PDFTK
[http://www.paehl.de/pdf/gui_pdftk.html](http://www.paehl.de/pdf/gui_pdftk.html)

Qoppa PDF Studio
[http://www.qoppa.com/psindex.html](http://www.qoppa.com/psindex.html)

---

### Post by nortexoid on 2009-04-04
> **aquascrotum said:**
> Has anyone come across a better PDF editor than the "PDF Editor" app?

I need an equivalent of Adobe Acrobat - I don't need to edit the pdf per say, just add/remove/compile pages that can vary in page size. PDF editor seems pretty rubbish at that unfortunately.

Any advice appreciated...

If I need to do advanced pdf editing I boot into Windows and use Acrobat Pro. However, I've found Foxit PDF Editor to work nicely under Wine for doing simple things, such as the tasks you mention. It crops pages too but only one page at a time.

PDF Editor is mostly unusable, if you ask me.

---

### Post by nortexoid on 2009-04-04
> **kaibob said:**
> Your question is a common one in this forum, and I have never seen anything that really meets your needs. There is a commercial product that will do what you want, and another Java-based one. Just do a search of the entire forum on the word pdfedit, and you'll find many threads on this issue.

I use PDF documents a lot and have finally settled on the command-line tool pdftk. This is far from an ideal solution, but I have yet to find anything better.

Anyways, do a search on pdfedit and see what other forum members have suggested.

EDIT:

GUI for PDFTK
[http://www.paehl.de/pdf/gui_pdftk.html](http://www.paehl.de/pdf/gui_pdftk.html)

Qoppa PDF Studio
[http://www.qoppa.com/psindex.html](http://www.qoppa.com/psindex.html)

PDF Studio looks reasonable.

---

### Post by Ben Crisford on 2009-04-04
You can export openoffice files as PDF, and Scribus works great for me as an editor.

Its in the repos.

```
sudo apt-get install scribus
```

---

### Post by rizitis on 2009-04-04
Try PDF-Shuffler 

[http://sourceforge.net/projects/pdfshuffler](http://sourceforge.net/projects/pdfshuffler)

 ubuntu 8.10 you can add repositories
```
deb http://ppa.launchpad.net/logari81/ubuntu intrepid main
deb-src http://ppa.launchpad.net/logari81/ubuntu intrepid main
```

and then 
```
sudo apt-get install pdfshuffler
```

I found it very, very useful

---

### Post by Racecar56 on 2009-04-04
OpenOffice can create PDF's but I don't think it can edit them.
You can write a PDF with the PDF button.
[Screenshot of the PDF button.]("http://img19.imageshack.us/img19/5540/openofficepdfbutton.png")
Also useful to transfer plain-old text files to PDF's.

EDIT: first post of 2nd page

---

### Post by hyper_ch on 2009-04-05
I use Cabaret Solutions:  [http://www.cabaret-solutions.com/en/downloads/linux](http://www.cabaret-solutions.com/en/downloads/linux)

You need to switch to german otherwise you'll get an error (the tool itself is in english). The form musst not be filled in, you'll just need to press the "Ich stimme zu" button. As said, in the english interface you'll get an error if you press the "I agree" button.

---

