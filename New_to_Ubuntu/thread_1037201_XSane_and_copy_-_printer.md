---
title: "XSane and copy - printer?"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by bodam on 2009-01-11
So how come XSane seems to be the only default app that doesn't use printers the same way as all the other apps?   I created a printer and everything else (OpenOffice, Firefox, et al) has no problems printing to it, but when my wife asked for me to copy something for her, when I tried to use the "copy" feature of XSane it didn't work.  I figured it would be just a matter of telling it which printer to use (I have two) so I opend up the config and all there is a section to type in a printer name and command.  This is where I'm lost. So how do I set it up?  As a work around, I saved the scan and then printed from GIMP but, it can't be this hard.

---

### Post by NewJack on 2009-01-16
Let's start with this....

What printer are you using?

---

### Post by bayvista on 2010-04-28
Hi,

I'm, using a Canon LBP3100. I have installed the drivers and it is working fine. In Xsane, I went to Setup/Copy and specified a new printer as LBP3100. The command to print I entered is: lpr -P LBP3100.

When I try to copy something, the scanner scans and transfers something to the print Q. However, that is where it stays. Nothing prints.

Any suggestions welcome.

---

### Post by Suncat2000 on 2011-04-06
I had a similar problem. I recently updated XSane to version 0.997, somewhere along my upgrade path from Ubuntu Karmic Koala to Maverick Meerkat. I tried to use the XSane Copy configuration and hit Scan, the print job was sent to the printer (I saw the status lights on the printer flash) but it would not print anything.

I played around with the commands in the Copy Setup and eventually found out the document that was being sent to the printer was PostScript 3 with zlib compression enabled.

The problem turned out to be that my printer, an HP Laserjet 1320, doesn't understand PostScript 3 with zlib compression.

I disabled the checkbox labeled *Create zlib compressed postscript image (PS level 3) for printing* in the XSane Copy setup.

Solved!:) With zlib compression turned off, my printer was able to understand the file and print the copy.

@bayvista and @bodam: The print command is the same command you would type at a shell prompt to print a file from the standard input. The following command is an example:
[FONT="Courier New"]$ **ls | lp -d myprinter -t "Copy to myprinter" -n 2**[/FONT]

The directory listing command, [FONT="Courier New"]ls[/FONT], executes a directory listing and [FONT="Courier New"]|[/FONT] pipes (redirects) its output to the input of the following program on the command line. The print command, [FONT="Courier New"]lp -d myprinter[/FONT], creates a print job and sends it to the printer named [FONT="Courier New"]myprinter[/FONT], with the job title "Copy to myprinter". The copies option, [FONT="Courier New"]-n 2[/FONT], makes it print two copies.

So in the XSane Copy setup, for the *myprinter* printer selection, you would enter [FONT="Courier New"]lp -d myprinter -t "Copy to myprinter"[/FONT] in the *Command* field. Enter [FONT="Courier New"]-n[/FONT] in the *Copy number option* field; XSane will add the number from the *Set number of copies* field in the scanner window.

---

### Post by asphixmx on 2012-09-13
Thanks to Suncat200, now I can copy from my scanner to the printer. I am using Fedora 17. Thank you!!!

---

