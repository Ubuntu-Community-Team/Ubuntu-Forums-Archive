---
title: "Printing - book mode?"
date: 2011-04-28
forum: New to Ubuntu
---

### Post by wep940 on 2011-04-28
I don't have a clue here, so I'm looking for some help here.  I downloaded the official Royal Wedding programme from the Royal Wedding web site for my sister.  It is in PDF format, 28 pages total.  My printer (HP Photosmart Plus B209a) doesn't have a "book" mode in the options for printing.  My brother in-law said he used to do that type of thing with PageMaker in Windows.  So, I'd like to find a Ubuntu/Linux app that would allow me to "print through it" (i.e., a "printer" that can be selected) that would allow me to print the PDF and have it come out in book mode.  There are 28 pages total, and they are 8 1/2 by about 5 1/2, so I need the book mode so that everything comes out in order, double-sided print, so I can just staple it in the center and give it to her.
 
I hope this makes sense - if not, please let me know.
 
Thanks in advance!!

---

### Post by KL_72_TR on 2011-04-28
I don't know if I'm helping at all, but I found these two links: [http://ubuntuforums.org/showthread.php?t=140815](http://ubuntuforums.org/showthread.php?t=140815) 
[https://help.ubuntu.com/6.10/ubuntu/serverguide/C/cups.html](https://help.ubuntu.com/6.10/ubuntu/serverguide/C/cups.html)

---

### Post by wep940 on 2011-04-30
Well, so far it looks like I'm out of luck.  I even installed Scribus since it is a psuedo PageMaker.  It seems the biggest problem is getting something to import a PDF file.  The next problem is getting it to understand that if I have 28 pages, and want to print them 2-up, double-sided, to understand that page 1 and a blank page go on the front side of my first sheet, while page 2 and page 28 go on the back side of the sheet, etc., working in towards the middle (hence book mode).  I just haven't found a way to do that.
 
Thanks for the links, and any addiditional help would be greatly appreciated.  I just double-sided printed the document to give to my sister for yesterday, but now I'm on a quest to learn more, and in particular, how to do this in Linux.

---

### Post by oldfred on 2011-04-30
I saved these links, do not know if they will work for you or not.

Print alt pages to make booklets:
Postscript
[http://dsl.org/cookbook/cookbook_25.html](http://dsl.org/cookbook/cookbook_25.html)
Scribus
[http://ospublish.constantvzw.org/tools/how-to-print-a-booklet-in-16-steps](http://ospublish.constantvzw.org/tools/how-to-print-a-booklet-in-16-steps)

---

### Post by dingodog on 2011-04-30
use (with wine):

***pdfbklt***
- [http://goo.gl/ojST](http://goo.gl/ojST)

```
wine pdfbklt -l -b A4 -p2s file.pdf
```

_[COLOR=Red]work on a copy, since ***pdfbklt*** overwrites its input file[/COLOR]_

---

### Post by Ken UK on 2011-04-30
So it has manual duplex support but I noticed it requires a specific driver. Maybe you need to install the official Linux drivers if you haven’t already?

---

### Post by wep940 on 2011-04-30
The driver works fine, and yep, manual duplex - print odd pages, reinsert the pages, print even pages.  In one of the links posted by oldfred there is a way to do it - just rather involved.  Following that page I install xpdf-utils, but still work required.  It will convert PDF to text, and there is another sub-program that extracts images.  So, I would need to extract the text, extract the images, then rebuild the pages again.  Then I have to convert to PS output, run it through another subprogram to get the book option.

I'm just on the quest now - since there is a way to do it via multiple steps, I'm hoping I can find some editor or word processor that can open a PDF file and then has the option to convert it to book format.  It's not as simple as duplex printing - it's 2 pages to a side, duplex, and book mode.  Maybe someone has some automated way of doing this.

Thanks for the help so far, and hoping more pointers come in.

---

### Post by yager01 on 2011-04-30
Have you installed the HPLIP driver for HP printers?  I have found that it gave me all the capabilities of my Officejet that is available in Windows but was missing with the driver that comes with Ubuntu.
Here is a link to the page to download the complete driver.
[http://hplipopensource.com/hplip-web/models/photosmart/photosmart_plus_b209a-m.html]("http://hplipopensource.com/hplip-web/models/photosmart/photosmart_plus_b209a-m.html")

---

