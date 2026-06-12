---
title: "PDF version converter"
date: 2009-12-02
forum: New to Ubuntu
---

### Post by pixideps on 2009-12-02
Hi all!
first I have to admit that I am quite a newbie in linux world
So does anybody know any tool that can convert 1.4. pdf version to 1.3 (of course working under ubuntu)
Namely I've used pdftk (with really nice gui pdfmanager) to split some 1.3 pdf files which worked perfectly but pdftk saved new pdfs in 1.4. version
which is (I know) better but my web application does not wont to work with versions greater than 1.3.
so, is there any solution to convert these files to 1.3 version under ubuntu or I have to stick to Adobe Acrobat
please any help ...

---

### Post by unik999 on 2009-12-02
hello at basic step   download the[COLOR=Yellow] [COLOR=Red]PDF Version Converter 2.01 [/COLOR][/COLOR]with help of which u can convert any version of pdf .
or visit at [COLOR=Red]pdf-tools.com[/COLOR] for more tools.

---

### Post by niteshifter on 2009-12-02
Hi,

Convert the 1.4 format to postscript via pdftops:
```
pdftops file14.pdf file.ps
```

Then convert the postscript to version 1.3 with ps2pdf13:
```
ps2pdf13 file.ps file13.pdf
```

pdftops is part of poppler-utils, you probably already have it ... if not install by:
```
sudo apt-get install poppler-utils
```

ps2pdf (and ps2pdf12, ps2pdf13 ps2pdf14) are scripts supplied with the ghostscript package. Install by:
```
sudo apt-get install ghostscript
```

After installing see:
```
man pdftops
man ps2pdf
firefox file:///usr/share/doc/ghostscript/Readme.htm

```

---

### Post by pixideps on 2009-12-02
> **unik999 said:**
> hello at basic step   download the[COLOR=Yellow] [COLOR=Red]PDF Version Converter 2.01 [/COLOR][/COLOR]with help of which u can convert any version of pdf .
or visit at [COLOR=Red]pdf-tools.com[/COLOR] for more tools.

But this tool is for windows?? and if I have to go with MS Win then I'll rather use acrobat ...

---

### Post by pixideps on 2009-12-02
Thanx a lot - I've done everything you've written 
but when I try to convert pdf to ps I get massage "Could not opent *.pdf"
what can I do?
poppler-utils and ghostscript are updated ...

---

### Post by kaibob on 2009-12-02
> **pixideps said:**
> ...So does anybody know any tool that can convert 1.4. pdf version to 1.3 (of course working under ubuntu)...

I believe ghostscript will do what you want. To give this a try, enter the following in a terminal window. Change input.pdf and output.pdf to whatever is applicable.

```
gs -sDEVICE=pdfwrite -dCompatibilityLevel=1.3 -dNOPAUSE -dQUIET -dBATCH -sOutputFile=output.pdf input.pdf
```

BTW, ghostscript often gives error messages when working with PDF files not produced with ghostscript. Normally you can just ignore these.

---

### Post by skalka on 2010-10-15
Thanks I was looking for this since a long time.

---

### Post by bpalone on 2012-05-03
I know this is an old thread, but thought I would post a link to a GUI I wrote to do this type of conversion, using Ghostscript.  It is available over at SourceForge.net, at the following link:

[http://sourceforge.net/projects/pdfvcon/?source=directory](http://sourceforge.net/projects/pdfvcon/?source=directory)

I still need to get some documentation up for it, but it is so simple that it really doesn't need any.  Except if you wanted to recompile it to change the default version, then it might be nice to be pointed to the places to make the changes.

It is called "pdfvcon" and pronounced PDF-Vee-Con.

Hope it is of some use to other people than just me.

---

