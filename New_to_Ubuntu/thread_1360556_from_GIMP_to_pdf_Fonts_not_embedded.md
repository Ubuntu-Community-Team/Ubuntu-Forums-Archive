---
title: "from GIMP to pdf: Fonts not embedded?"
date: 2009-12-21
forum: New to Ubuntu
---

### Post by ginestre on 2009-12-21
Hello

I have a graphics file that I am required to provide in pdf format. I made it in GIMP, and converted to pdf using ImageMagicK, just by following the menu tree (save as..... pdf)

When I sent the file to its destination website, I got an automated reply saying 'UPLOAD ERROR. You have not embedded all of the fonts used in the pdf file. Use the EMBED COMPLETELY ALL FONTS option in acrobat distiller. We require you to embed all fonts and not just the letters you ahve used'  

The help pages on the website just repeat the same message.

What should I do? What tool should I use?

TIA

---

### Post by Bucky Ball on 2009-12-21
I think there is an option when you save it out of GIMP that you might be missing. You need to flatten when you import it as a graphics file first.

Open the graphic in GIMP then export to whatever format (PNG, JPG) then just insert the file into an OOffice word or draw document.

... then save that to PDF (import also from memory) and email.

---

### Post by junapp on 2009-12-21
yes, you can flatten your image so the fonts are no longer really fonts etc, but you may also want to look into using Scribus if you have a requirement to embed the fonts in a pdf.

Depending how complex your graphic is, it may be a trivial task to put the image into scribus, and put the same text in. Scribus has some great features for sending a pdf off to the printers.

---

### Post by junapp on 2009-12-21
similar question and answer here:
[http://registry.gimp.org/node/11724](http://registry.gimp.org/node/11724)

---

### Post by ginestre on 2009-12-22
Thanks for the various suggestions. Flattening the GIMP image doesn't work- or at least, when I flatten it the fonts are not all embedded. And making a new file with the othe rprograms suggested, importing the GIMP image I had produced image (I tried as an xcf, a png, a jpg and a tif) and then exporting as a pdf has always left me with a problem of empty margins top and bottom and left and right, even when defining those margins as zero from within the programs. 

So I'm back to square one.

---

### Post by vanadium on 2009-12-22
I do not understand the issue. You are converting a bitmap graphic to PDF. Yet, a bitmap does not need any font to be displayed. So there is no reason to embed any font if all the PDF contains is bitmap graphics? I suspect an issue with the destination website rather than yourself creating a PDF.

---

