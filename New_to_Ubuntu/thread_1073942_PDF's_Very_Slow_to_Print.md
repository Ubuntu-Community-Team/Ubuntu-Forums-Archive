---
title: "PDF's Very Slow to Print"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by jeepfreak2002 on 2009-02-18
I just installed Ubuntu 8.10 64bit on a Core 2 Duo, 2 Gig RAM, 250 Gig SATA, Shuttle Mini PC.

PDF's are taking forever to print to a Lexmark Laser printer on a Linksys Print Server.  Other doc's ( or .odt's, I should say) or web pages from firefox print fine, but these PDF's are killing me.  

I am using the standard document PDF viewer that is standard, and I think that Adobe's "Reader" solved the prob for me before, but they do not support the 64bit OS, so I am stuck with the standard PDF viewer.  

Any Ideas????

---

### Post by cmnorton on 2009-02-18
How have you defined the printer in Ubuntu?

Have you tried printing PDFs to another printer?

This  could be the Lexmark drivers.

---

### Post by Bladeforger on 2009-02-18
Try epdfviewer.  It's the light version of Evince, and I have the same issue.

You can read my comments at this thread:

[http://ubuntuforums.org/showthread.php?t=1068935](http://ubuntuforums.org/showthread.php?t=1068935)

If you want, you can also experiment with the lpr command in bash.  That didn't work for me, but it might be a function of how much memory is available or something.

Also, and you probably do this anyway... count pages.  I've had epdfviewer and the lpr command both come up short on pages.  Happens.  With epdfviewer, you use the job tab and begin with the page after the one that printed last.  epdfviewer doesn't short me on pages often enough to be too much of a pain.

Adobe, by contrast, always prints each page--all the way through--but life is too frantic sometimes to wait 1-2 minutes per page.  And adobe doesn't collate--even if the box is checked.

epdfviewer WILL collate, but it's more likely to run out of memory halfway through and the print job dies.  I just do one after the other for multiple copies.  THAT seems to be better on the memory for some reason.

Hope this helps you.

Keith

---

### Post by scorchgeek on 2009-02-18
What sort of stuff is in the PDF? Sometimes PDFs can simply print slowly, even if they are opened with Adobe Reader and Windows.

---

### Post by Bladeforger on 2009-02-18
And I was going to say, Jeepfreak, I drive one too--when I'm not riding the KLR.

---

### Post by Bladeforger on 2009-02-18
> **scorchgeek said:**
> What sort of stuff is in the PDF? Sometimes PDFs can simply print slowly, even if they are opened with Adobe Reader and Windows.
For me, it's tax returns--form and numbers and all.  

And, also, another thought... can't you run the 32 bit on a 64 bit machine?  Seems like I read somewhere that you could and that there was better compatibility...

Keith

---

### Post by era86 on 2009-02-18
> **scorchgeek said:**
> What sort of stuff is in the PDF? Sometimes PDFs can simply print slowly, even if they are opened with Adobe Reader and Windows.

This is very true.  May not be an Ubuntu problem at all...  Where I work, PDFs print deathly slow.

---

### Post by jeepfreak2002 on 2009-12-04
alas, I still suffer from slow PDF printing.

I am now using 32bit Jaunty, and it is still deathly slow to print PDF's.

I am printing to Lexmark T642's which are on Linksys print servers.  They are set up as LPD printers to the correct IP address.  It seems that the print servers may have something to do with it, as my printing at home is fine.  Any experience improving the performance of print servers?

Documents and web pages print fine, just PDF's are slow.

jeepfreak

---

### Post by bkann on 2010-01-06
I am having what sounds like the same problem.  It takes as much as 15 minutes in between pages when I print PDFs to a networked Xerox N17 laser from 9.10.

While I don't have a solution for this, it does remind me of a Windows fix I encountered once.  My network users were having this exact same "slowness" problem printing PDFs from Windows.  In Acrobat, I found an option under File > Print > Advanced to "Print as Image."  As long as that was checked, the print jobs were speedy and we did not run into any memory issues.

Is it possibly a similar issue in Ubuntu?  If so, I have not found any comparable option to print as an image.  In lieu of a real fix, I've been printing PDFs from a virtualized Windows installation, which can be a pain but at least it prints fast.

Thanks for any help!

---

### Post by gsocker on 2010-01-06
"Print As Image" should be possible; however it would require the appropriate magic incantations to CUPS,ghostscript, and the printer driver - probably more trouble than it is worth. 
The reason the defaults are so slow with a laser:
Most inkjets, with the exception of a few high-end HPs, basically get "spray this color ink at this position".
Lasers, however, usually get "Print this shape at this position(may be defined elsewhere) using this font/line style/color..."
The result of this is that the laser has to generate the image itself. It also needs enough memory to hold the page image, as well as all the print data needed for at least a single page, plus any memory required by the  RIP(Raster Image Processor) software to generate the image.
Postscript is an actual programming language, and can actually be used to write programs as well as produce printouts. 
If it's slow, probably the document is complex enough the printer is having trouble with it - I one saw a PDF college map take 3 minutes for 1 page on my HP.
You might try lowering the resolution, or if possible, creating a printer entry using PCL instead of Postscript(if supported by the printer).  PCL should result in the computer doing most of the processing, instead of the printer.

---

### Post by bkann on 2010-01-06
Thanks, gsocker!  That's great information.  I haven't finished trying all your suggestions and toying around yet, but I have not seen a PCL driver for my printer yet.

I am curious about one thing, though.  Like other users who posted here, this slowness only occurs when printing PDFs.  If I print comparable material (eg., even graphic-heavy content) in the form of a document (.odt, .ods, etc.), a full-page graphic straight from GIMP, or Web content, it prints at what I would call 'normal' speed.  It seems only to be PDFs that give me trouble.  Is this consistent with the PS/PCL issue you mentioned?

Thanks again!

---

### Post by gsocker on 2010-01-06
Most likely - what is probably causing the problem isn't so much the graphics as the number of shapes. I'm not sure if you're familiar with the differences between vector graphics and bitmaps, but what is probably happening: the web pages contain a mix of text(sent to the printer as text), and images(sent to the printer as a bitmap).
On the other hand, PDF, although it can contain only bitmapped images, usually is composed mostly or entirely of vectors. There is a speed difference in handling some text with intermixed images vs a PDF page which may have upwards of 10,000 vector shapes which have to be processed into a bitmap by the printer before anything is printed. Since this processing tends to involve a lot of math, things can get slow.  Ever tried rendering a complex SVG image in Firefox or Inkscape? Same issue.

Most lasers support both PCL and Postscript.
Xerox says yours supports PCL5e, 6, and Postscript 3.
Try adding a printer with using "Generic" as the manufacturer, and "Generic PCL5e printer" as the model. This will loose you access to any fancy features on the printer, but it will at least let you see if the speed improves.
Note that you may have a slightly different model description; my main box runs Gentoo, and I don't use foomatic as,useful as can be, it isn't needed for my setup and causes more problems than is solves.

---

### Post by yavoh on 2010-01-27
I am indebted to you, @gsocker, because I finally tried this and it solved my problems.  I can finally print pdf's without waiting an infinite amount of time.

For the record, I have an HP LaserJet 1320 connected via USB.  With HPLIP installed, I chose the Generic -> PCL5e driver, and it just worked.  Magic!

(now just to fix that niggling flash issue...)

---

### Post by freak42 on 2010-01-27
just for the record, I have adobe reader V 9.2 (10/6/2009) up and running on 9.04 / 64-bit.

---

### Post by Tank! on 2010-03-07
> **gsocker said:**
> 
Try adding a printer with using "Generic" as the manufacturer, and "Generic PCL5e printer" as the model. This will loose you access to any fancy features on the printer, but it will at least let you see if the speed improves.

Thank you so much for posting this! It immediately solved my problem!:popcorn:

---

### Post by cacycleworks on 2010-03-07
Another few thoughts... 

I don't use the built in print to file PDF printer and instead will apt-get install cups-pdf. It isn't in the software center's list.

I've got 9.10 64 bit and have adobe. I forget if they've got the deb file or what... but lots of situations, I use 
```
sudo dpkg -i --force-architecture adobe_blah.deb
```

After installing the adobe reader, I will go back and switch the default program back to the gnome viewer, as adobe seems to make my computer(s) slow down too much. I'm occasionally forced to use it because of the PDF I'm trying to read.

:) Chris

---

### Post by fredfox1 on 2010-03-14
I had a pdf that took 33 minutes to send the first try to the printer when using evince, and then it was garbage. On a whim (previous solutions sounded complex), I installed xpdf. Since a link is not automatically created in Gnome, I opened the document using the command line:

xpdf <document-name>

The document was a complex map and it printed to my HP inkjet in about 30 seconds, most of which was printing time, not spooling. The print dialog indicated it was using lpr, but my distribution simply routed it to my printer. (only one printer installed on the machine)

Running Ubuntu Studio 64 bit, 9.10, printer HP Deskjet 952C connected via USB (just plug it in and it is available for printing)

---

### Post by lyall on 2010-03-14
The following is from Lexmark
I did a Google search for **Linux Lexmark pcl drivers**
find this link for a pdf file
[www.lexmark.com/publications/pdfs/print_drivers/en/ug.pdf]("www.lexmark.com/publications/pdfs/print_drivers/en/ug.pdf")

on page 11 of the pdf is the following
you might want to look at this pdf doc some more, for addition info

Installing on Linspire, Debian, or Ubuntu Linux
 1 Read &#8220;Before installing the printer drivers&#8221; on page 8.
 2 Make sure you have enough hard disk drive space in /usr/local to install the printer driver.
    For more information about finding more space, see &#8220;Finding space to install the printer drivers package&#8221; on
    page 13.
 3 Download the printer drivers package (print-drivers-linux-glibc2-x86.deb) from the Lexmark Web site at
    [http://www.lexmark.com/drivers](http://www.lexmark.com/drivers).
 4 Install the package file.
    # dpkg -i /tmp/print-drivers-linux-glibc2-x86.deb
 5 Run the following setup script to complete the installation:
    # /usr/local/lexmark/setup.lexprint
Note: Your specific printer driver may not be included in the standard package. Check the Software and
Documentation CD or the Lexmark Web site to determine if there are any software plug-ins available. For more
information, see &#8220;Plugin Manager utility (software updates)&#8221; on page 31.

good luck and have fun learning

---

### Post by twowheeler on 2010-03-15
Aside from the suggestions already made here, you should know that a few bugs have appeared in ubuntu lately which cause these symptoms.  Some are solved but some are not.  The one I have been watching is  [463059]("http://bugs.launchpad.net/ubuntu/+source/foomatic-filters/+bug/463059").

As noted there, the latest upgrade solved part of my issue but not all of it.  I will be posting another bug on this subject.  If you search launchpad, you will find others (with different printers) asking why PDFs are so slow to print.  

Good luck.

---

### Post by GrantsV on 2010-08-21
XPDF solved it for me, almost instant prints to my default printer.

---

### Post by Ivan.Calderon on 2010-09-24
This one worked for me:

[LIST=1]
[*]Use the "Print to file" printer choosing Postscript (.ps) format and give the file a location and name.

[*]Open the .ps file and print it. Presto!
[/LIST]

Printer: HP Deskjet D1560
CUPS version: 1.4.3
Ubuntu version: 10.04 32 bits. Up to date.

---

### Post by helpdeskdan on 2010-09-26
I did find that changing to pcl3 helped significantly, thanks gsocker.  Though it's still slow.  Also, printing draft quality seemed to speed things up on my ancient hp4050TN.  XPDF & printing to ps didn't help much for me.  Like acroread, they directly use lpr to print.

---

