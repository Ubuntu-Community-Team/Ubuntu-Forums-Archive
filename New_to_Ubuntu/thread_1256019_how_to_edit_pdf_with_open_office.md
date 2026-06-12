---
title: "how to edit pdf with open office?"
date: 2009-09-02
forum: New to Ubuntu
---

### Post by heyyy on 2009-09-02
whenever i try to open a pdf with open office i see some non-understandable characters
maybe its a encoding thing but i dont know
anyone who knows how to do it please reply

---

### Post by gradinaruvasile on 2009-09-02
PDF s are not made to be edited in first place. but they are means of editing them...

U have to use PDF importer plugin in Openoffice Draw. And it might not work as expected some times. But it is useful.


[http://extensions.services.openoffice.org/project/pdfimport](http://extensions.services.openoffice.org/project/pdfimport)

---

### Post by gandaran on 2009-09-02
> **heyyy said:**
> whenever i try to open a pdf with open office i see some non-understandable characters
maybe its a encoding thing but i dont know
anyone who knows how to do it please reply

I believe you have to install the pdf extension as root on open office for it to work properly.

---

### Post by keiichidono on 2009-09-02
[http://pdfedit.petricek.net/en/index.html](http://pdfedit.petricek.net/en/index.html) Might be your bowl of soup.

---

### Post by aeiah on 2009-09-02
openoffice handles editing pdfs through the plugin mentioned, and in my experience is easier to use and gets better results than inkscape, but depending on the quality of your document and the editing that you need to do you may find inkscape better in some circumstances. 

also its worth noting that if you have access to an xps printer, the xps format is a lot nicer to play with on a low level than pdf. its got an open file structure similar to ODF (ie, its basically a .zip file with xml files inside)

---

### Post by stinger30au on 2009-09-02
pdftk is the go

sudo apt-get install pdftk

[http://www.pdftk.com/](http://www.pdftk.com/)

---

### Post by aeiah on 2009-09-02
> **stinger30au said:**
> pdftk is the go

sudo apt-get install pdftk

[http://www.pdftk.com/](http://www.pdftk.com/)

only good for merging, splitting etc. but it is great, yes.

jpdfteak is another decent multiplatform pdf manipulator that i end up having to use a fair bit.

---

### Post by Ms_Angel_D on 2009-09-02
What extactly do you mean bye edit? 

if you only need to fill out PDF forms you can install flpsed from the Synaptic package manager. It's a pdf annotator that allows you to add text to PDF documents.

But if you need actually edit Full PDF documents as someone mentioned before you should check out PDFedit or perhaps [Scribus]("http://www.scribus.net/")

you can also install them by clicking the links I provided below or by searching the synaptic package manger.

[LIST]
[*][Scribus]("apt://scribus")
[*][PDFedit]("apt://pdfedit")
[*][Flpsed]("apt://flpsed")
[/LIST]

---

### Post by sydbat on 2009-09-02
> **heyyy said:**
> whenever i try to open a pdf with open office i see some **non-understandable characters**Have you installed msttcorefonts? (System > Administration > Synaptic)

Often a document (like a PDF) was created by a Microsoft Office product and you need these fonts to read it. Might help your "non-understandable characters" problem.

---

### Post by Bartender on 2009-09-02
I tried pdfedit a few weeks ago.  It was a horrible experience.  I couldn't tell where the text would end up until I finished typing and put it on the page.  Ended up typing and re-typing the same line over and over.
After an hour of struggling just to fill in a dozen lines or so, I realized that pdfedit was not recognizing the "j" key.  Plugged in a USB keyboard, same thing.

That was it. Pdfedit was removed from the PC.  Good riddance.

---

### Post by mike555 on 2009-09-02
After installing the "import pdf" plugin to Open office you will need to tell it to open pdf files using the drop-down menu , otherwise you get jibberish .......

---

