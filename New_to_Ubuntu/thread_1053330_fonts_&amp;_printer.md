---
title: "fonts &amp; printer"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by HiHoStevo on 2009-01-28
Okay I have been using Ubuntu 8.10 for at least 10 minutes now...sorry I feel lot like Alice tumbling down the rabbit hole.

When I open up the word processor (open office) it does not show any fonts.. although when you type it obviously has some type of a display font as you can see what you are typing.  Why can I not see what fonts are installed?

When I attempt to print a test page, the print dialogue box comes up but all fields are completely blank.  If I just hit return (there is a highlighted button... with no text or description) it does run a page through the printer........ which is blank, but that may be because this particular printer has not been used in several months.

Okay cleaned up the printer head and I now have the usb printer and network printers functioning... but when pulling up the print dialog box it is still just full of empty rectangles.

Even the save dialog box selections are all empty... I must be missing some type of display fonts or something..........???

Is there a guide that helps with all this basic stuff?

Yes, I did download the .pdf file of the getting started book listed in the permanent links... however it does not address this issue at all.

---

### Post by HiHoStevo on 2009-01-28
Okay... Under System/Preferences/Appearance there is a font tab with numerous fonts listed for windows or documents etc.........

However no matter which font I select the entire menu system in OpenOffice word processor or spreadsheet is blank... there is a dash where the menu and file selections should be, but other than that nothing.

I am sure someone must know why these openoffice applications have no fonts and because no font you cannot select any menu items whatsoever as you cannot see what they might be......... weird.

---

### Post by Coreigh on 2009-01-28
Sanity check questions:

0. Do you have Ubuntu installed or are you working from the LiveCD?

1. With the word processor open, the text across the title bar (very top of the window) says "Openoffice.org Writer"

2. Given #1 is true; in the toolbars  at the top of the window the box that would say the name of the current font is blank or empty? What about the Formatting label to the left and the font size to the right of the font namee box?

---

### Post by HiHoStevo on 2009-01-28
> **Coreigh said:**
> Sanity check questions:

0. Do you have Ubuntu installed or are you working from the LiveCD?

1. With the word processor open, the text across the title bar (very top of the window) says "Openoffice.org Writer"

2. Given #1 is true; in the toolbars  at the top of the window the box that would say the name of the current font is blank or empty? What about the Formatting label to the left and the font size to the right of the font namee box?

Yes 8.10 is installed on the computer not being run from CD.

Top line is Untitled 1 - OpenOffice.org Writer (it is version 2.4 if that matters)

Current font is blank as are all other boxes... if you click on the box for about 1 nanosecond you can see the name of a font Times Roman but then it is gone.  

All of the Menu bars across the top File Edit View ... etc all all missing and in their place is a dash.... if you click on the Dash where file should be then a menu drops down with many selections also blank some with small icons on the left most just dashes...

I followed directions in the getting started book and created a .fonts folder in the home folder and transferred in the TrueType fonts from another windows machine... no change.

If you run your mouse over one of the icons in the toolbar... it pops up a little descriptor window... but it is also blank.

---

### Post by cariboo on 2009-01-28
You obviously have a problem with your Open Office installation. I would suggest reinstalling it to see if that makes a difference.

Go to System-->Administration-->Synaptic Package Manager, and type open office in the search bar. Right-click on all the open office entries that are marked as installed and select reinstall.

As a side note, do you have your printers setup properly? Go to System-->Administration-->Printing to make sure.

Jim

---

### Post by HiHoStevo on 2009-01-28
> **cariboo907 said:**
> You obviously have a problem with your Open Office installation. I would suggest reinstalling it to see if that makes a difference.

Go to System-->Administration-->Synaptic Package Manager, and type open office in the search bar. Right-click on all the open office entries that are marked as installed and select reinstall.

As a side note, do you have your printers setup properly? Go to System-->Administration-->Printing to make sure.

Jim

Both installed printers are working fine, but the print dialog boxes in any open office application are all blank... I will try your suggestion to re-install...... are the .cab files on the hard drive as someone else did the original installation on this computer for me??

---

### Post by HiHoStevo on 2009-01-28
I did as you instructed and found that their were a number of OpenOffice.org packages... several of them marked with a solid green box on the left... those I can do a re-install on... however the first two items OpenOffice.org was the first just had an open box next to them where only Install could be selected.  When I clicked the install button on this first file it brought up a secondary dialog box listing other files that this would change... I told it to go ahead and it is now downloading an extra 105 megs or so... we will see what happens...

As I am so new please excuse the silly question, but is there just a single installer file for OpenOffice that I can download and install where it asks questions during installation about which features I would like installed... (sort of like what would happen with MS Office installation?

---

### Post by HiHoStevo on 2009-01-28
Okay after the install and re-install finished I opened up the word processor again... and still no fonts, no menu items, etc

---

### Post by HiHoStevo on 2009-01-28
I downloaded version 3.0 of openoffice and attempted to install it...

But received this error

Error: Failed to extract Java Runtime Environment (JRE) files. Exit Code Error 7

---

### Post by sandyd on 2009-01-28
well at least we know whats wrong now...
somethings wrong with java or its missing.....


installing sun-java6-bin should solve the problem (or reinstalling it)

openoffice is built on java ;)

install java, then go and download the DEBS for openoffice here
[http://download.openoffice.org/other.html](http://download.openoffice.org/other.html)


and heres the fastest way to install openoffice from the download....

extract everything to the desktop...
Open up the folder and go into "DEBS"
theirs a folder called "desktop-integration"

open it up, and drag it into the DEBS folder 

navigate to the "DEBS" directory through the terminal

type this in
[code]
rmdir desktop-*
dpkg -i *
[code]

that will get openoffice rolling

---

### Post by HiHoStevo on 2009-01-28
> **carlee said:**
> well at least we know whats wrong now...
somethings wrong with java or its missing.....


installing sun-java6-bin should solve the problem (or reinstalling it)

openoffice is built on java ;)

install java, then go and download the DEBS for openoffice here
[http://download.openoffice.org/other.html](http://download.openoffice.org/other.html)


and heres the fastest way to install openoffice from the download....

extract everything to the desktop...
Open up the folder and go into "DEBS"
theirs a folder called "desktop-integration"

open it up, and drag it into the DEBS folder 

navigate to the "DEBS" directory through the terminal

type this in
[code]
rmdir desktop-*
dpkg -i *
[code]

that will get openoffice rolling

Alright I will see if I can locate the proper version of Java to install...

Thanks for the office link..........

I don't suppose they have a version that just has a simple setup or install icon  :)

My fortran days were a long time ago......

ok... got Java 6 installed... man installing stuff in linux is like going back in time 30 years...

I suppose that is the price we must pay to get away from the Microsoft Monster... hee hee.

---

### Post by HiHoStevo on 2009-01-28
> **carlee said:**
> 
Open up the folder and go into "DEBS"
theirs a folder called "desktop-integration"

open it up, and drag it into the DEBS folder 



I really appreciate the help and assistance, but if I find the desktop-integration folder in the DEBS folder... how or why would you drag it to the DEBS folder?? Sounds to me like it is already inside the DEBS folder unless I am missing something (which is quite likely).

Also.........

What does [code] mean???

---

### Post by HiHoStevo on 2009-01-28
> **carlee said:**
> 

extract everything to the desktop...
Open up the folder and go into "DEBS"
theirs a folder called "desktop-integration"

open it up, and drag it into the DEBS folder 

navigate to the "DEBS" directory through the terminal

type this in
[code]
rmdir desktop-*
dpkg -i *
[code]

that will get openoffice rolling

Please excuse my ignorance Carlee... I do appreciate the guidance.  However, did I mention I have used Ubuntu for less than an hour?

when I type in your command rmdir desktop -* I get this response:

rmdir: failed to remove `desktop-*': No such file or directory

I have the file on my desktop named "OOo_3.0.1_LinuxIntel_install_en-US_deb.tar.gz"

When I tell it to extract the entire file to the desktop I wind up with these two additional files:

OOO300_m15_native_packed-1_en-US.9379 (2)
jre-6u11-linux-i586.bin

It appears that it just duplicated the original file with a small name change... and then added the .bin file on the desktop.

I am assuming that your "*" in your command line is shorthand for a file name I am supposed to recognize... and the [code] command is something else you thought I might already understand........

Which of course I don't......... unfortunately......

---

### Post by HiHoStevo on 2009-01-29
Well after 3 re-installs of Ubuntu I found the problem.......

The Hardware manager suggests installing an Nvidia graphics driver (96) and after it is installed is when the menu's disappear!!!

---

