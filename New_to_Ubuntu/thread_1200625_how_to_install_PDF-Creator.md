---
title: "how to install PDF-Creator"
date: 2009-06-30
forum: New to Ubuntu
---

### Post by aadx on 2009-06-30
Hi,

I am a newby with Linux, Ubuntu in particular.
I know that it is possible to export documents to pdf files, such as with OpenOffice. With windows I used PDF-Creator. I was very happy with that. Because I find PDF-Creator produces neater and smaller files I would like to use it with Ubuntu too.

Therefore, on **[http://linux.softpedia.com](http://linux.softpedia.com)**, under its **tab Linux**,  I downloded the archive **ipdf-1.0.0.tar.gz**  of PDF-Creator.

However, though I searched for teachings thereof on Internet, this forum inclusive, I was unable to figure out how to install that application.

Can anyone please tell me how to install said packet of PDF-Creator, possibly of any tar.gz packet in general?

Thanks in advance,
Aad

---

### Post by Mornedhel on 2009-06-30
You don't need it. Ubuntu can print PDFs out of the box, just select the PDF printer when you try to print a file.

---

### Post by aadx on 2009-06-30
Mornedhel,
I knew that. That's called "exporting¨ in Ubuntu, as I mentioned. But I am not satisfied with the result. Therefore I would like to use PDF-Creator.

Oh, my printer list does not include a pdf-printer, but only my inkjet printer. I installed Ubuntu last week. Maybe it is different from your version.

Besides, learning how to install/use and install pack like  **ipdf-1.0.0.tar.gz**  of PDF-Creator will familiarize me more with Ubuntu. That is what I want most.

Aad

---

### Post by Cheesehead on 2009-06-30
The easy way to add a PDF-printer to your printer list is to add the 'cups-pdf' package. It's not an exporter - it processes the postscript file just like a printer, and it does create remarkably small PDF files.

You can use PDF Creator, if you wish. Since it is a Windows application, you must install Wine first. Then download the PDF Creator installer to your desktop, right-click on it, and open it using Wine.

---

### Post by cbtengr on 2009-06-30
> **aadx said:**
> Mornedhel,
I knew that. That's called "exporting¨ in Ubuntu, as I mentioned. But I am not satisfied with the result. Therefore I would like to use PDF-Creator.

Oh, my printer list does not include a pdf-printer, but only my inkjet printer. I installed Ubuntu last week. Maybe it is different from your version.

Besides, learning how to install/use and install pack like  **ipdf-1.0.0.tar.gz**  of PDF-Creator will familiarize me more with Ubuntu. That is what I want most.

Aad

Read this thread:

[http://ubuntuforums.org/showthread.php?t=1196983&highlight=install+tar.gz](http://ubuntuforums.org/showthread.php?t=1196983&highlight=install+tar.gz)

---

### Post by Paqman on 2009-06-30
> **aadx said:**
> Mornedhel,
Oh, my printer list does not include a pdf-printer, but only my inkjet printer. I installed Ubuntu last week. Maybe it is different from your version.


Choose "print to file" then select .pdf as the file type. This is not the same as exporting a file as .pdf in Open Office.

---

### Post by aadx on 2009-06-30
Thanks for all replies.

I am sorry to say that I found the thread mentioned by cbtengr confusing.
The tar.gz file of pdf-creator I downloaded did not contain an install or exe file as I was used to with Windows. I could not apply Wine with it. It contained files with "odd" extensions I never saw before. Could they be files for UNIX/LINUX systems? Anyhow, it did contain a Read file with in it the instruction to run config. I found a file with that name in the same folder. I ran it. Something happened in the folder, but I can't say what exactly. It did not provide a pdf-printer.

I tried to print a document as a file also. However, that did create a PS file (it is the only type I can choose). A PS file is not what I want.

Than I ran Synaptic Packetmanagement where I found cups. I installed it (all kinds of stuff automatically also). Then I found a "printer" called plain PDF in my printer list. I tried to print with it, which I think it did. However, I cannot find the location where it put the pdf file. Besides, it didn't asked for a name for the "printed" pdf file nor a location to put it. Does any of you have an idea what I can try next?

Aad

---

### Post by Paqman on 2009-06-30
> **aadx said:**
> 
I tried to print a document as a file also. However, that did create a PS file (it is the only type I can choose). A PS file is not what I want.


Change the file type option from .ps to .pdf in the print window. 
[IMG]http://ubuntuswitch.files.wordpress.com/2009/02/bildschirmfoto-drucken.png?w=500&h=371[/IMG]

---

### Post by tarps87 on 2009-06-30
I can't find the exact program you are trying to install, could you please post a link to the download.
Usally once you have untared the file there will be a file called README or some form of readme.
The common steps are
./configure,make,make install
or if there is a .bin file you will need to run it

---

### Post by aadx on 2009-06-30
See my opening question. 
I came on the site and the file mentioned therein by searching on Google for "pdf creator linux"

---

### Post by aadx on 2009-06-30
Paqman,
I have a very different print window:
[IMG]http://www.aadx.nl/Afdrukken.png[/IMG]

As I said before, I installed Ubuntu/Gnome last week. Therefore, I suppose I have the latest version. So I cannot choose the think you advised.
Aad

---

### Post by niteshifter on 2009-06-30
> **aadx said:**
> ...
Than I ran Synaptic Packetmanagement where I found cups. I installed it (all kinds of stuff automatically also). Then I found a "printer" called plain PDF in my printer list. I tried to print with it, which I think it did. However, I cannot find the location where it put the pdf file. Besides, it didn't asked for a name for the "printed" pdf file nor a location to put it. Does any of you have an idea what I can try next?
Aad

CUPS will drop the output pdf file into the PDF folder in your home folder. You need to make this folder:
```
mkdir PDF
```
Yes, must be PDF, not Pdf or pdf. 

Some other tools you need:

pdftk - Do anything to the file, burst it, rotate it, change fields (Title, Author, etc.) and more. Command line tool, available via Synaptic or:
```
sudo apt-get install pdftk
```
There's a GUI front end for it (not in the repositories) "out there", but it's not the easiest to work with.

PDF Editor (package name: pdfedit) -  Useful for editing pdf files directly. But you need to be familiar with the internals of a pdf document (it's object model). Get via Synaptic or:
```
sudo apt-get install pdfedit
```

ImageMagick (should already be installed) - Very handy when working with images and pdf files. pdftk will "liberate" images from a pdf, ImageMagick goes the other way - image -> pdf (the convert tool, specifically). Point your browser to file:///usr/share/doc/imagemagick/www/index.html

Then there's Ghostscript (already installed). Do anything with any PostScript / PDF. Steep learning curve, however. There's a raft of conversion scripts supplied with it - ps2pdf, pdftops, pdfopt - type this on a command line to get an idea:
```
apropos pdf
```
Point your broser to file:///usr/share/doc/ghostscript/Readme.htm for an overview.

---

### Post by aadx on 2009-06-30
To summarize:
- Using "Synaptic management" I installed "cups-pdf" package.
- In my personal (home) folder I made folder PDF (capitals only). First I used mkdir PDF in a terminal window. Then I renamed it and made a new folder PDF in the same way as I was used to do with Windows. I printed pdf's in both cases. Both turned out to work properly. I wonder why CUPS did not made such folder by itsself and why, since it did not made it, did not notify me that such folder had to be made.
- I printed and exported the same doc file and later the same odf file (saved from said doc file) as pdf's. Identical, same sized pdf's were created.
- I started this thread with a question about how to install PDF-Creator. That is a Windows program I used before and by which I made a pdf from the same doc file mentioned before.
It turned out that the file made by PDF-Creator was 20% (40 Kbyte) smaller than those created by printing or exporting in Ubuntu.

- As adviced by niteshifter I also ran in a terminal window: sudo apt-get install pdftk
Though it installed I could not find anything I could pdftk start/open/apply with.
- pdfedit could be installed from "Add/Remove" in the main menu. Indeed, it seems pdfedit is something for specialists only. 

Conclusion:
For the time being I prefer _exporting_ a document as a pdf file rather than _printing_ it as a pdf because with exporting the resulting file can be found in the same folder as the original file. The size of the pdf will be the same.
Editing a pdf remains a thing to investigate.

Thanks all of you for the assistance.
[IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]
Aad

---

### Post by kaibob on 2009-07-01
> **aadx said:**
> ...- As adviced by niteshifter I also ran in a terminal window: sudo apt-get install pdftk
Though it installed I could not find anything I could pdftk start/open/apply with....

Pdftk is a command-line tool. You will not find anything to "start/open/apply" pdftk.

[http://www.accesspdf.com/pdftk/](http://www.accesspdf.com/pdftk/)

There is a GUI frontend for pdftk, but I haven't used it and some people have reported problems with it.

[http://www.paehl.de/pdf/gui_pdftk.html](http://www.paehl.de/pdf/gui_pdftk.html)

---

### Post by Mornedhel on 2009-07-01
> **aadx said:**
> It turned out that the file made by PDF-Creator was 20% (40 Kbyte) smaller than those created by printing or exporting in Ubuntu.

I would like to point that many Windows PDF printers assume that most fonts used are available everywhere and do not bundle them all with the PDF. This does result in smaller documents, but also in ugly default fonts when the document is rendered on a system that does not, in fact, have those fonts.

---

### Post by Paqman on 2009-07-01
> **aadx said:**
> 
As I said before, I installed Ubuntu/Gnome last week. Therefore, I suppose I have the latest version. So I cannot choose the think you advised.


I suspect you've got Hardy (Ubuntu 8.04) rather than the latest, Jaunty (Ubuntu 9.04). When you go to System > Admin > System Monitor > System, what release does it say?

---

### Post by aadx on 2009-07-01
Ubuntu
version 9.04 (jaunty)
Kenel Linux 2.6.28-13-generic
GNOME 2.26.1

---

### Post by bartora on 2010-04-01
Hi!

I had a trouble similar to [aadx]("http://ubuntuforums.org/member.php?u=865749"). Here I could not found the place where cups was throwing the pdf files. This is because cups needs a directory called PDF on the user's home folder. So then i created this folder called PDF, and everything worked fine. Now it's possible to generate pdf docs from any other documente by printing. The resulting pdf is located in the PDF folder in user's home.

---

### Post by daoes on 2010-04-01
Thanks its really help newbie like me

---

