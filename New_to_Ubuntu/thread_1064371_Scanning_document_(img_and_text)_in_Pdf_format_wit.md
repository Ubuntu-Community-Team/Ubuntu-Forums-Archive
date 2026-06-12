---
title: "Scanning document (img and text) in Pdf format with selectable text?"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by LastWho on 2009-02-08
Hi,
Is it possible to scan documents (which contain images and text) in pdf format and make the text selectable? 

ubuntu 8.04 user
thanks


(ps: I have Hp 1100 multifunction, and i m used with it native software running under windows to scan documents in pdf format with selectable text and image)

---

### Post by blueridgedog on 2009-02-08
You might get good results (not the exact results you are looking for) by using tesseract-ocr to convert the PDF to text.

Here is a good description:

[http://www.groklaw.net/articlebasic.php?story=20061210115516438](http://www.groklaw.net/articlebasic.php?story=20061210115516438)

You can install it with:

```
sudo apt-get install tesseract-ocr 
```

You will also need ghostscript and pdf2tif.

---

### Post by LastWho on 2009-02-08
Hi Blueridgedog,
Thank for your answer, but my major concern is to get a big PDF file in which i ll be cabable to "select - copy text" also to "search" for keywords

a text file is not really what i m looking for! because i ll lose the structure and the look of the original document
thx

---

### Post by blueridgedog on 2009-02-08
I agree...

You will need a PDF tool with build in OCR (like acrobat).  Scribus may have potential:

[http://www.scribus.net/](http://www.scribus.net/)

---

### Post by LastWho on 2009-02-09
> **blueridgedog said:**
> I agree...

You will need a PDF tool with build in OCR (like acrobat).  Scribus may have potential:

[http://www.scribus.net/](http://www.scribus.net/)
hi, thanks for theses propositions, i already have acrobat with utilities and it doesn't recognize the text, 
the Scribus i don"t know how to use it in that purpose

---

### Post by blueridgedog on 2009-02-10
Scribus can export a PDF, and potentially import text/images from a scanner.

---

