---
title: "PDF Creator for Linux?"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by baxna on 2009-04-27
In Windows I use a wonderful open source program called PDFCreator. It installs like a regular printer, and lets you print anything directly to PDF (browser windows, text files, images, command prompt windows, etc.). Is there something easy to use like this for Ubuntu/Linux? I've tried looking through the Add/Remove programs window but can't find anything that sounds close.

On the [PDFCreator website]("http://www.pdfforge.org") I have the option of downloading the source code, however I've never messed with this and have no idea how to compile/install a program from source. That is, unless one of you kind & helpful members have the patience to explain to to a newbie!

Thanks for your suggestions, Mike

---

### Post by MyR on 2009-04-27
cups-pdf ?

---

### Post by mcduck on 2009-04-27
Ubuntu already has the ability to print to PDF. No need to install anything extra for that. ;)

In the print dialog select the "Print to File" as the printer, and you can choose where to save the file and which format you want to use (PDF or Postscript).

---

### Post by MyR on 2009-04-27
> **mcduck said:**
> Ubuntu already has the ability to print to PDF. No need to install anything extra for that. ;)

In the print dialog select the "Print to File" as the printer, and you can choose where to save the file and which format you want to use (PDF or Postscript).

really? I didn't think cups-pdf was installed by default anymore.

---

### Post by mcduck on 2009-04-27
> **MyR said:**
> really? I didn't think cups-pdf was installed by default anymore.

It's not. The PDF printing is handled directly by Cairo.

---

### Post by Wiebelhaus on 2009-04-27
You can also edit them if I'm not mistaken , At least in my scripted installs i"m installing something I've been using for years that allows me to edit them after printing.

---

### Post by baxna on 2009-04-27
I tried doing that several times and selected the PDF option. However, either it produced a white sheet or no file ever appeared-- either in my home directory or the desktop?? Do I need to install cups, or is it already on there by default?

---

### Post by mcduck on 2009-04-27
> **baxna said:**
> I tried doing that several times and selected the PDF option. However, either it produced a white sheet or no file ever appeared-- either in my home directory or the desktop?? Do I need to install cups, or is it already on there by default?

Works fine on my machine.

But if you can't get it to work, then install cups-pdf and use that instead.

---

### Post by Dragonbite on 2009-04-27
> **sx66gns said:**
> You can also edit them if I'm not mistaken , At least in my scripted installs i"m installing something I've been using for years that allows me to edit them after printing.

What was it you installed, and is it command-line or a full GUI?

---

### Post by baxna on 2009-04-27
> **mcduck said:**
> But if you can't get it to work, then install cups-pdf and use that instead.

How do you install cups-pdf?

---

### Post by Wiebelhaus on 2009-04-27
> **Dragonbite said:**
> What was it you installed, and is it command-line or a full GUI?

Let me try to figure out what it is..

---

### Post by Wiebelhaus on 2009-04-27
> **sx66gns said:**
> Let me try to figure out what it is..

I found it , see I install from a huge script and only update it when necessary.

```
sudo apt-get install pdfedit
```

So I end up with relatively the same installation after new releases.

---

### Post by mlentink on 2009-04-27
for cups-pdf:
System>Administration>Synaptic Package Manager
search for cups-pdf, select and apply

---

### Post by listerdl on 2009-04-27
open office has an in-built pdf creator i am sure of it....

---

### Post by Wiebelhaus on 2009-04-27
> **listerdl said:**
> open office has an in-built pdf creator i am sure of it....

Yea , you can export any doc or sheet into pdf and it works like a perfectly!

---

### Post by stchman on 2009-04-27
> **baxna said:**
> In Windows I use a wonderful open source program called PDFCreator. It installs like a regular printer, and lets you print anything directly to PDF (browser windows, text files, images, command prompt windows, etc.). Is there something easy to use like this for Ubuntu/Linux? I've tried looking through the Add/Remove programs window but can't find anything that sounds close.

On the [PDFCreator website]("http://www.pdfforge.org") I have the option of downloading the source code, however I've never messed with this and have no idea how to compile/install a program from source. That is, unless one of you kind & helpful members have the patience to explain to to a newbie!

Thanks for your suggestions, Mike

PDF creation is included standard on Ubuntu since Hardy I believe.

Openoffice has a PDF export tool built in.  Also if you go to File--->Print there will ne an option to Print to File.  Selecting that you have two options, PS and PDF.  Select PDF and a target folder.  Simple as pie.

---

### Post by gandaran on 2009-04-27
> **sx66gns said:**
> I found it , see I install from a huge script and only update it when necessary.

```
sudo apt-get install pdfedit
```

So I end up with relatively the same installation after new releases.
pdfedit is a qt aplication, xournal is a nice gtk application for gnome users that can also edit pdf's

---

### Post by baxna on 2009-04-27
> **stchman said:**
>  Also if you go to File--->Print there will ne an option to Print to File.  Selecting that you have two options, PS and PDF.  Select PDF and a target folder.  Simple as pie.

Yes I tried doing it that way. Once a blank file showed up, it was all white with no text or graphics. The other two times no file showed up at all, even though I changed the destination location.

---

### Post by anjilslaire on 2009-04-27
You can also get down-n dirty, and simply name the file name.pdf

I've donme that on ocasion, and the file opens in a regular pdf viwer as if it was created properly. I have yet to see any corruption from simply renaming th extension.

That being said, I usually do a Print to File > and save as a .pdf as mentioned earlier in the thread.

---

### Post by Wiebelhaus on 2009-04-27
> **gandaran said:**
> pdfedit is a qt aplication, xournal is a nice gtk application for gnome users that can also edit pdf's

Yea , But Xournal is kinda quirky. It won't allow you to just select text and delete it then re write whatever it is you know , it's just weird.

---

### Post by SaintDanBert on 2010-01-28
> **mcduck said:**
> It's not. The PDF printing is handled directly by Cairo.

I continue to use cups-pdf on Ubuntu Karmic.
I'm not familiar with [highlight]cairo[/highlight and PDF printing. 
While I go do some research on this "cairo" thing, please explain for me and others in this thread.

~~~ 0;-Dan

===========================
Follow-UP
===========================
I found information about a libcairo2 library for 2D graphics.
[http://packages.ubuntu.com/karmic/libcairo2](http://packages.ubuntu.com/karmic/libcairo2)

I found reference to Cairo-Dock an animated launcher.
[http://blog.theunical.com/ubuntu/how-to-install-cairo-dock-on-ubuntu-9-10-usb-pen-drive-linux-2/](http://blog.theunical.com/ubuntu/how-to-install-cairo-dock-on-ubuntu-9-10-usb-pen-drive-linux-2/)

---

### Post by frenchn00b on 2010-01-28
> **baxna said:**
> In Windows I use a wonderful open source program called PDFCreator. It installs like a regular printer, and lets you print anything directly to PDF (browser windows, text files, images, command prompt windows, etc.). Is there something easy to use like this for Ubuntu/Linux? I've tried looking through the Add/Remove programs window but can't find anything that sounds close.

On the [PDFCreator website]("http://www.pdfforge.org") I have the option of downloading the source code, however I've never messed with this and have no idea how to compile/install a program from source. That is, unless one of you kind & helpful members have the patience to explain to to a newbie!

Thanks for your suggestions, Mike


```
apt-get install cups-pdf  
```  # cups-pdf - PDF printer for CUPS
then you add it as GENERIC printer with kprinter 
or 
apt-get install printconf 
apt-get install system-config-printer xprint-common 
then 
system-config-printer 

then print on PDF

even better
you can print from console
run my script for futher info:
[http://easyldap.exofire.net/files/installer/](http://easyldap.exofire.net/files/installer/)

---

### Post by lifeboy on 2012-04-16
This thread is quite old already, but allow me to add some thoughts and comments to it.

I've been using Ubuntu for a long time now, but there are distictly lacking features within cups-pdf.

1. The windows pdfcreator app has a great feature that allows you to pause the printer, then print all the stuff you want from any app and then combine the various file and generate one pdf doc.  cups-pdf and libreoffice/openoffice lacks that.  You have to drop to command line to do that and then it's really geek territory.

2. pdfcreator does allow a lot of options to be set from the gui.  

[INDENT]
[LIST]resolution - cups-pdf does as well[/LIST]
[LIST]graphics format - cups-pdf doesn't[/LIST]
[LIST]pdf forms - cups-pdf doesn't[/LIST]
[LIST]pdf version - cups-pdf doesn't[/LIST]
[/INDENT]

to name a few.  Geeks can combine and possibly/probably find other options, but what about ordinary desktop users?

3. The other programs that I have tried out are just bad or barely ok when is comes to combining pdf's.  The java monstrosities are just a no-go area as far as I'm concerned.

So while it is possible to output from one app into pdf, with varying output quality (cups-pdf being the poorest and libreoffice the best as far as I can tell), to do more than that is not something you can quickly do when you want to send someone a document.  It requires too much schlep, and isn't productively useful.
:frown:

---

### Post by oldos2er on 2012-04-16
Closed. Please don't bump old threads.

---

