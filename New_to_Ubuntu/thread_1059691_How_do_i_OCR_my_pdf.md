---
title: "How do i OCR my pdf?"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by gackt on 2009-02-04
I need to run ocr for my pdf. It contain more than 100 pages so taking its screenshot and run ocr one by one is sound stupid, is there any way to do this more quickly. Ohh i wish there is some pdf reader with ocr integrated in it (is there anything like this in ubuntu?)

---

### Post by Roger Mudd on 2009-02-04
Is your PDF a scan or was it created digitally (saved as a PDF out of OO Writer, for example)? If it was created digitally you may be able to simply highlight, copy and paste the text directly out of the PDF into a text or word processing document using Evince or Acrobat. If scanned, you'll probably have to look into some of these applications:

[http://groundstate.ca/ocr?page=1](http://groundstate.ca/ocr?page=1)

Looks like they have a relatively simple command line interface that would go something like this:
```
ocrprogramname original.pdf output.txt
```
Can't speak as the efficacy of the applications as I haven't used them, but it should be possible.
You may also want to look into gscan2pdf. I use it for scanning documents to PDF from a hardware scanner, but I think you can actually load PDF files into it for OCR purposes. It's GUI front end may be more appealing to some.

---

### Post by ProgramErgoSum on 2009-02-04
In Synaptic, I can see packages for [gocr]("http://jocr.sourceforge.net/") and [tesseract]("http://code.google.com/p/tesseract-ocr/"). I haven't used them but you might want to have a look into those packages and see if it helps.

---

### Post by gackt on 2009-02-04
Thanks guys but it seem that most of them will only convert from image not pdf.

---

### Post by 3rdalbum on 2009-02-04
Gocr is pretty hopeless in my experience, unless I'm using it wrong.

If you have a copy of Adobe Acrobat (the full program, not the reader) you might be able to install it in Wine. It has an excellent OCR function - so good that some printing shops simply scan into PDF format and use Acrobat's OCR function instead of a dedicated OCR program.

---

### Post by Roger Mudd on 2009-02-04
Look at this article from Groklaw:

[http://www.groklaw.net/articlebasic.php?story=20061210115516438](http://www.groklaw.net/articlebasic.php?story=20061210115516438)

It discusses the use of Tesseract for a similar purpose. I believe Google uses Tesseract for it's book scanning, so I assume it should have the capabilities you require.

---

