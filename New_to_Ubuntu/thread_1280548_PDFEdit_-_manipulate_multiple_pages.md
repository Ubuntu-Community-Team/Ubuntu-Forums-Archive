---
title: "PDFEdit - manipulate multiple pages"
date: 2009-10-02
forum: New to Ubuntu
---

### Post by expatCM on 2009-10-02
I have just been playing with PDFEdit. I am probably working the program the wrong way since I can only manipulate one page at a time.

I open the file and go to Page / Page Transformation / Page Translate and then change the ty value to -50 and the page drops to where I need it.

However .... this only applies to one page and I have a lot of them. I am now looking for a setting to apply the transformation to all page in the document rather than just one.

man pdfedit is rather brief.  I can see that there is also a command line operation but I cannot see if the syntax will apply to all pages in a document.

Can anyone tell me how to run a page translate that applies to all pages rather than just the one viewed?

---

### Post by expatCM on 2009-10-07
Any ideas on this at all .... ?  The developers have a moderated list but it does not appear to be active ....

---

### Post by entropy1 on 2009-10-07
I've never been able to do anything with PDFedit.

However, to do simple things (insert pages, delete pages, extract pages), I like pdfshuffler.  It has a gui interface.  You can download the .deb file from
[http://sourceforge.net/projects/pdfshuffler/](http://sourceforge.net/projects/pdfshuffler/)
Then double click on the .deb file to install.

When the gui of pdfshuffler is not convenient for large files,
I prefer the command-line utility pdftk, which you can install using synaptic.  Useful commands can be found at
[http://www.accesspdf.com/pdftk/](http://www.accesspdf.com/pdftk/)

An example of using pdftk to rotate all even pages by 180 degrees can be found at
[http://ubuntuforums.org/showthread.php?t=927940&highlight=pdf-shuffle](http://ubuntuforums.org/showthread.php?t=927940&highlight=pdf-shuffle)

---

### Post by expatCM on 2009-10-07
I found PDFEdit to be very good but I simply cannot work out how to apply transformation changes to all pages rather than one.

I did not know about pdfshuffler, it is an interesting application for basic manipulation.  Sadly it does not answer my need but it is good to know about this.

pdftk is something I have installed already but this unfortunately does not help my need.

I wonder if I am going about this the wrong way.  Perhaps I would be asking if anyone knows of an application that will increase the page border of a print job ....

---

### Post by entropy1 on 2009-10-07
You might be able to do what you want with gsview.
[http://pages.cs.wisc.edu/~ghost/gsview/](http://pages.cs.wisc.edu/~ghost/gsview/)

---

### Post by expatCM on 2009-10-08
GhostView ....  well never heard of it until now so thanks for the suggestion.  It appears in the repositories as gv.

I have installed it and am in the learning curve.  I get the idea that this is likely to help but I really need to find out how to do things first, it is not so straight forward ...

---

### Post by expatCM on 2009-10-08
When using GhostView, how do you save the file so that it saves your changes (either as a new file or the opened file)?

When I use "Save All" or "Save Marked" I get either a zero byte file or a very small file saved and a message saying that the file name could not be found.

---

### Post by entropy1 on 2009-10-08
Ghostview is not the same as gsview:
[http://pages.cs.wisc.edu/~ghost/gsview/get49.htm](http://pages.cs.wisc.edu/~ghost/gsview/get49.htm)

I have trouble installing gsview since I do not see it in the repository.

I used gsview mostly under windows.  So you could try that just to see if gsview can solve your problem.

---

### Post by expatCM on 2009-10-08
ooops ... well that is not so clever of me.  I think I made the error when I searched Synpatic.

I have downloaded the .tar.gz and unpacked it but the install instructions are something I cannot cope with ....  they really are lacking ....  it is no way a matter of running configure / make / make install ... 

If you know of an idiots guide to installing this ....  erm ... I think I could use it ... 

It seems that there have also been changes in what you can download, previously there was an rpm for download which you could change to a deb with Alien but that is no longer the case.

---

### Post by entropy1 on 2009-10-08
Try using the windows version under wine.  Even though I have a 64-bit machine and OS, only the 32-bit versions of gs and gsv installed properly under wine.

First install gs and then gsv under wine.  Start up gsview and open the .pdf file.  Under File, select "convert".  Click the
"properties" button.  At the bottom of the dialog box are places to type in your desired page offset in points.  Click OK.  Back in the "convert" dialog, click OK.  Then give output file name and click on "save"

Maybe this will help.

---

### Post by expatCM on 2009-10-08
Well like you said the 64 bit version does not install under Wine ....  I tried it.  The download of the 32 bit version took me 5 attempts, on what appears to be a very slow server, before I could get a copy that was not corrupted .....

Installed and followed your suggested instructions (which are really essential).  This worked like a charm and I have exactly what I need now for the final pdf.

Thank you very much for telling me about gsview and for making sure that I got it working.

---

### Post by tacantara on 2009-10-08
> **entropy1 said:**
> I've never been able to do anything with PDFedit.

However, to do simple things (insert pages, delete pages, extract pages), I like pdfshuffler.  It has a gui interface.  You can download the .deb file from
[http://sourceforge.net/projects/pdfshuffler/](http://sourceforge.net/projects/pdfshuffler/)
Then double click on the .deb file to install.

When the gui of pdfshuffler is not convenient for large files,
I prefer the command-line utility pdftk, which you can install using synaptic.  Useful commands can be found at
[http://www.accesspdf.com/pdftk/](http://www.accesspdf.com/pdftk/)

I just downloaded PDF Shuffler, as I was actually searching for a program that would place separate PDF pages in one file.  The largest compile I attempted was 8 pages, and it handled that quite well.  That particular file ended up being about 735 KB, and it was put together quickly.

---

