---
title: "Printer solution?"
date: 2010-02-22
forum: New to Ubuntu
---

### Post by nene7 on 2010-02-22
Hi to all,
 I use my printer in windows and the programs that they come with the printer let me option to scan pager and convert to document. Does xsane or other open source program let me do this?

---

### Post by natravis on 2010-02-22
[http://www.sane-project.org/sane-mfgs.html](http://www.sane-project.org/sane-mfgs.html)

Check that list against your device ... and remember, we can only help you with a problem if you give us relevant information, like the scanner you are trying to use, your version of linux, etc.

---

### Post by nene7 on 2010-02-22
Sorry,
 My printer is HPC4200, it work fine need just do some work in pdf to odt. natravis the page give it printer support on xsane but i dont know convert .pdf to .odt or .doc i just want if i can do the convertion. 

Thank

---

### Post by ajgreeny on 2010-02-22
It sounds as if you need some **O**ptical **C**haracter **R**ecognition (OCR) software, which will scan the printed PDF, and turn it into text.  Linux is not well served with OCR packages, but I find the best is tesseract, a command line application.  You will need to scan the PDF, saving the image as a .tif (this is important, all other image formats, including .tiff will fail) then use command ```
tesseract file.tif outtext
```which will turn the file.tif into a txt file called outtext.txt.  It may sound complicated, but once you are used to it you will find it is quite easy, and quick to do.

You may also find that you can simply highlight the text in a pdf file and copy it as text to an openoffice file, or you can try the pdfimport extension for openoffice, which I've never got to work, though I have not tried lately.

A search in synaptic for **pdf** also throws up lots of possible packages including pdfedit, which might just do what you want.  I've never tried any of them so have no real idea if they do what you are hoping for.

---

