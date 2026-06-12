---
title: "OCR + Tesseract + DJVU to PDF?"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by disappearedng on 2009-04-14
Hey everyone
How do I convert a djvu file (all images) to a pdf text file? I have tesseract installed.

---

### Post by blueridgedog on 2009-04-17
Have you tried simply printing the djvu file to a PDF using the print to file tool built in to Ubuntu?

---

### Post by rdelcueto on 2009-06-18
I use the following script: [DjVu files/OCR with Tesseract]("http://en.wikisource.org/wiki/Help:DjVu_files/OCR_with_Tesseract")

Save the script into a file and make it executable.
Then run the script passing as first argument the path to your djvu file.

You need the djvulibre-bin and tesseract-ocr packages.

---

