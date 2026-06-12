---
title: "Evince failed to open PDF correctly"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by Albert Net on 2009-12-27
I can open the PDF file, but the display is quite disappointing.

The letters in one words have some conjunction. Quite annoying.

Attachment is how it looks like.

It shows perfectly in windows.

---

### Post by gsmanners on 2009-12-27
It is annoying when you get those non-standard pdfs, but you can use Acrobat in Linux.

Acrobat is available outside the normal repository. See [https://help.ubuntu.com/community/AcrobatHowTo](https://help.ubuntu.com/community/AcrobatHowTo)

---

### Post by Albert Net on 2009-12-28
How do you know the PDF is non-standard?


Detailed information about this "non-standard" PDF:

Producer: Acrobat Distiller 4.0 for Windows
Creator:   Microsoft Word 9.0

I think that is all related.

Another standard PDF, which can be opened by evince correctly, has the following property:

Producer: BCL easyPDF 4.30 (0409)
Creator:   Print2PDF 5.0.06.0426 by Software602

Possibly that is the reason, but can someone tell me what is the difference between producer and creator?

Above all, the "non-standard" PDF can be open in windows correctly, which is sort of unfair, I think.

---

### Post by gsmanners on 2009-12-28
It isn't the OS that is to blame. The problem lies in the difference between the way Evince and Acrobat work. Acrobat uses proprietary technology and Evince does not. It's pretty simple, really.

---

### Post by Albert Net on 2009-12-28
Probably, you are wrong. 

Under windows, I use Sumatra to view the "non-standard" pdf, and it works just fine.
Sumatra is an open source tool, so proprietary technology you mentioned is not true. Otherwise, Sumatra will fail as well.

I think the "non-standard" pdf is created under windows. Therefore, I can't view it correctly under Ubuntu.

Just personal opinion.

---

### Post by hugmenot on 2009-12-29
Can you make a screenshot of »Document properties«, the »Fonts« tab?

---

### Post by Sir Jasper on 2009-12-29
Hi,

FoxitReader v 1.1.0 (debian version is lean and fast) may be worth a try, else the Portable version of Sumatra works using Wine.

My regards

---

### Post by philinux on 2009-12-29
> **Albert Net said:**
> I can open the PDF file, but the display is quite disappointing.

The letters in one words have some conjunction. Quite annoying.

Attachment is how it looks like.

It shows perfectly in windows.

Enable the partner repo in your software sources and install acroread.

---

### Post by niteshifter on 2009-12-29
Hi,

PDF Creator: The software that generated (created) the stream of data that was fed to the Producer software - which creates the "instructions" (how to draw) the PDF. PDFs internally are quite complicated beasts, a reader application functions in a manner not to dissimilar to a virtual machine.

gsmanners is partly correct: It's not the OS. hugmenot is on track - it's the fonts specified for use in the document, it (or they) are not present on your system so a substitute font of similar - but not exact same - metrics is being used.

The package msttcorefonts may help to fix this, but if Word was using some "specialty" or third-party font that was installed on the originating system then msttcorefonts won't have it. Won't hurt to install it, and even if the exact font isn't found, it may yield a font that's a better fit.

---

### Post by meho_r on 2009-12-29
As pointed out, nothing to do with OS or Evince. It is definitely fonts problem. There are still people who do not embed fonts (for whatever reason) or fonts themselves do not allow embedding.

---

### Post by Albert Net on 2010-01-04
This is the screenshot of the property of the PDF file.

There is no "font" tab.



After installing msttcorefonts, the display is normal finally. 


There is still one doubt left. 

When I was reading one latex tutorial, it says the difference between DVI and PDF is that PDF needs more disk space, for it contains all the necessary fonts within the document, so we will not have any problem of portability.

Since PDF contains the fonts, why do I need to download the fonts?

---

### Post by hugmenot on 2010-01-04
Albert, not that properties window

Press Alt-Enter in Evince, then Fonts

---

### Post by Albert Net on 2010-01-04
I got it. Thank you, hugmenot.

It says that the fonts are not embedded. That explains why it doesn't work with msttcorefonts.

I guess the PDF is not created with pdflatex, for all necessary fonts will be embedded when it is created using pdflatex.

I hope I am right.

---

