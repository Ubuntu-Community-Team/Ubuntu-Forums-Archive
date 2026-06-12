---
title: "how to convert pdf to word"
date: 2009-09-11
forum: New to Ubuntu
---

### Post by kousbi on 2009-09-11
hello everybody i am new here and i have a problem
i tried to convert o pdf file to doc or rtf with open office but didn't work.
any advice?
thanks in advance

---

### Post by perce on 2009-09-11
I think koffice can do something like that, but I don't know how well. pdf is not meant for that.

---

### Post by mediax on 2009-09-11
There are a number of utilities for converting pdf to text, html, etc in the repositories.

I'm at work at the moment, so I'm afraid I can't be specific, but if you do a search for pdf in Synaptic you should find them.

Which version of Open Office are you using?  Being able to edit pdf files is supposed to be one of the big developments in Open Office 3.

---

### Post by Excedio on 2009-09-11
> **mediax said:**
> There are a number of utilities for converting pdf to text, html, etc in the repositories.

I'm at work at the moment, so I'm afraid I can't be specific, but if you do a search for pdf in Synaptic you should find them.

Which version of Open Office are you using?  Being able to edit pdf files is supposed to be one of the big developments in Open Office 3.

I've tested the Open Office .pdf import feature, it works but it's crazy slow (probably because it's hell of a process). Even though it was slow, It worked.

[Check...check check check...check it out!]("http://extensions.services.openoffice.org/project/pdfimport") (ummm...click on that...)

---

### Post by philinux on 2009-09-11
The import extension is in synaptic. The pdf gets imported into OO Draw.

---

### Post by aeiah on 2009-09-11
open office 3 pdf conversion is the best ive come accross, although im no expert. its nicer than inkscape or pdf to html conversions but yes, it is indeed slow. there'll be a way to automate a batch of them and leave it running for a while

---

### Post by L Campbell on 2009-09-11
> **kousbi said:**
> hello everybody i am new here and i have a problem
i tried to convert o pdf file to doc or rtf with open office but didn't work.
any advice?
thanks in advance

I did a little searching and found this:-

[http://www.pdftodocconverterpro.com/?gclid=CJyY3evY6ZwCFQ_xDAodg3KwjA](http://www.pdftodocconverterpro.com/?gclid=CJyY3evY6ZwCFQ_xDAodg3KwjA)

It appears as though it might be what you want but I haven't tried it out myself.

Hope it helps you.

---

### Post by tomazaz on 2009-09-11
Online service which do conversion from PDF to DOC perfectly [http://www.freepdfconvert.com/convert_pdf_to_source.asp]("http://www.freepdfconvert.com/convert_pdf_to_source.asp")

---

### Post by oldfred on 2009-09-11
Some PDF's are text based and easy to convert others are graphics.

Some alternatives:
man page pdftotext

sudo apt-get install poppler-utils
pdftotext {[COLOR=#6666CC]PDF-file[/COLOR]} {[COLOR=#6666CC]text-file[/COLOR]}

Or try this (you need pdfimages, imagemagick and, of course, tesseract):

pdfimages -j {[COLOR=#6666CC]PDF-file[/COLOR]} {[COLOR=#6666CC]text-file[/COLOR]}
for i in *.pbm; do convert $i $i.tif; tesseract $i.tif $i; done

---

### Post by kousbi on 2009-09-11
thanks everybody i will try and answer back

---

### Post by joinoi on 2009-09-22
I use this pdf to word converter freeware. [http://www.hellopdf.com](http://www.hellopdf.com). It can convert all pages of pdf to word.

---

