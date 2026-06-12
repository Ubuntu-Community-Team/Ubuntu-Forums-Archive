---
title: "Convert webpage to PDF"
date: 2009-06-30
forum: New to Ubuntu
---

### Post by mevets on 2009-06-30
I want to be able to put the android developer guide onto my G1. the best way to do this is to convert the webpage into a pdf. Adobe has an online converter but it doesnt include pictures and it mangles the formatting. Does anyone know if I can convert the website into a pdf on Linux?

---

### Post by ad_267 on 2009-06-30
Is it all on one page? You could install the cups-pdf package and then print the page using the PDF printer.

---

### Post by steveneddy on 2009-06-30
Click file --> page setup --> select Format For: PDF

Click Apply

File --> Print --> Select PDF

Look in your home folder - folder named PDF - should be in there

this may be a few steps too many, but it works.

---

### Post by thatDougore on 2009-07-01
If you're using Firefox you could install the PrintPDF add-on: [https://addons.mozilla.org/en-US/firefox/addon/5971?src=api](https://addons.mozilla.org/en-US/firefox/addon/5971?src=api)

./Doug

---

### Post by mevets on 2009-07-01
The problem is that I need links to be followed. I ended up using webhttrack which is a cmdline tool for this sort of thing.

---

### Post by sybille on 2009-07-01
Hi,

Htmldoc is another option. I find it works well for w3c compliant pages but can have some problems with web pages with funky coding. It can produce PDFs with live links, and it's available in the Ubuntu repositories.

[http://www.htmldoc.org/](http://www.htmldoc.org/)

---

### Post by binbash on 2009-07-01
> **sybille said:**
> Hi,

Htmldoc is another option. I find it works well for w3c compliant pages but can have some problems with web pages with funky coding. It can produce PDFs with live links, and it's available in the Ubuntu repositories.

[http://www.htmldoc.org/](http://www.htmldoc.org/)

I will check it out, thanks

---

### Post by colau on 2009-07-01
> **mevets said:**
> I want to be able to put the android developer guide onto my G1. the best way to do this is to convert the webpage into a pdf. Adobe has an online converter but it doesnt include pictures and it mangles the formatting. Does anyone know if I can convert the website into a pdf on Linux?
```

sudo aptitude install cups-pdf

```
From the browser's File>Print selecting PDF click print.
In your home folder see the PDF directory.

---

### Post by Paqman on 2009-07-01
Ctrl-P > Print to file > Output format = .pdf

Job done.

---

### Post by sybille on 2009-07-01
Hi, everyone.

Using cups-pdf or the regular print to PDF within Firefox is fine if you do not need a PDF file with live links, that is, links that can be clicked in the PDF and open in a browser.

mevets asked about an application to make a PDF that includes live links (and images with good formatting). I'm not familiar with webhttrack (I tend to use either Zotero or just wget to save web pages), which is what mevets ended up using, but I do know that htmldoc gives pretty good results on most pages.

---

